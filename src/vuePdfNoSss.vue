<style src="./annotationLayer.css"></style>
<script>
import componentFactory from './componentFactory.js';
import pdfjsWrapper from './pdfjsWrapper';

const PDFJS = require('@themainstage/pdfjs-dist/build/pdf.js');
const PDFJSWorker = require('worker-loader!@themainstage/pdfjs-dist/build/pdf.worker.js').default;

if ( typeof process == 'undefined' || process.env.VUE_ENV !== 'server' ) {
  if ( typeof window !== 'undefined' && 'Worker' in window && navigator.appVersion.indexOf('MSIE 10') === -1 ) {

    PDFJS.GlobalWorkerOptions.workerPort = new PDFJSWorker()
  }

  var component = componentFactory(pdfjsWrapper(PDFJS));
} else {

  var component = componentFactory({});
}

export default component;
</script>
