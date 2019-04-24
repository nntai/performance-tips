IMPROVE WEBSITE PERFORMANCE TIPS

For React + Webpack(meteor) project

# MEASURE TOOLS

- [Google Chrome Lighthouse (Audits)](https://developers.google.com/web/tools/lighthouse/): You will get information about loading time and some suggestions to improve performance.

- You could use one of [these methods](https://medium.com/@joeclever/three-simple-ways-to-inspect-a-webpack-bundle-7f6a8fe7195d) to get information about your webpack's bundle file (all modules (and its related modules) sizes). The less bundle file is, the less time  download it.

- For meteor project, you could use [bundle-visualizer](https://docs.meteor.com/packages/bundle-visualizer.html).


# TIPS:

## 1. After get information about your webpack's bundle file, you should:
  - Remove unused package inside bundle file.
  - Remove similiar packages (eg: underscore & lodash) and use only one.
  - Replace big package with smaller one.

## 2. Use webpack's [optimization attribute](https://webpack.js.org/configuration/optimization/) to [split](https://webpack.js.org/guides/code-splitting/), [minimize](https://webpack.js.org/configuration/optimization/#optimizationminimize) bundle file.

## 3. Optimize using [Lodash](https://www.blazemeter.com/blog/the-correct-way-to-import-lodash-libraries-a-benchmark) and [moment](https://github.com/jmblog/how-to-optimize-momentjs-with-webpack). 

## 4. [Lazy load your component](https://blog.logrocket.com/lazy-loading-components-in-react-16-6-6cea535c0b52)
  - [react-loadable](https://github.com/jamiebuilds/react-loadable#readme). You could check `swiss-getal` project how to use it.
  - [React's core API](https://blog.logrocket.com/lazy-loading-components-in-react-16-6-6cea535c0b52)

## 5. Optimize Images:
  - Reduce file's size using TinyPNG(https://tinypng.com/), it also supports JPG files.
  - Lazy load image using [lazysizes](https://github.com/aFarkas/lazysizes).

## 6. Apply suggestions from Google's Chrome Lighthouse (Audits) result.

## 7. Async loading script:

  Eg: Instead of loading stripe script in HTML file, we will load its in `componentDidMount`:
  ```code
    componentDidMount() {
      const stripeJs = document.createElement('script');
      stripeJs.src = 'https://js.stripe.com/v3/';
      stripeJs.async = true;
      stripeJs.onload = () => {
        // The setTimeout lets us pretend that Stripe.js took a long time to load
        setTimeout(() => {
          this.setState({
            stripe: window.Stripe(apiKey),
          });
        }, 500);
      };

      if (document.body) {
        document.body.appendChild(stripeJs);
      }
    }
  ```

## 8. Using CDN or moving your host/DB location 😂

## 9. Using Loading Indicator

  This method didn't improve performance, reduce loading time but makes user feeling better.

# React tips (continue)

