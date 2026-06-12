---
title: "WebKit Problem"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by Bit-Devil on 2014-03-07
Hello,

I try to compile WebKit ([https://help.ubuntu.com/community/WebKit](https://help.ubuntu.com/community/WebKit)) on Ubuntu 12.04 LTS .
Afte a while a compile error appears:

  CXX      DerivedSources/JavaScriptCore/libjavascriptcoregtk_3_0_la-InspectorJSBackendDispatchers.lo
  CXX      DerivedSources/JavaScriptCore/libjavascriptcoregtk_3_0_la-InspectorJSFrontendDispatchers.lo
  CXX      DerivedSources/JavaScriptCore/libjavascriptcoregtk_3_0_la-InspectorJSTypeBuilders.lo
  CXX      DerivedSources/JavaScriptCore/libjavascriptcoregtk_3_0_la-JSCBuiltins.lo
  CXXLD    libjavascriptcoregtk-3.0.la
  CXX      Source/WebKit/gtk/WebCoreSupport/libwebkitgtk_3_0_la-TextCheckerClientGtk.lo
  CXX      Source/WebKit/gtk/WebCoreSupport/libwebkitgtk_3_0_la-AcceleratedCompositingContextGL.lo
In file included from Source/WebKit/gtk/WebCoreSupport/AcceleratedCompositingContext.h:23:0,
                 from Source/WebKit/gtk/WebCoreSupport/AcceleratedCompositingContextGL.cpp:20:
./Source/WebCore/platform/graphics/GraphicsLayer.h:401:37: error: 'PlatformLayer' has not been declared
./Source/WebCore/platform/graphics/GraphicsLayer.h:407:38: error: 'PlatformLayer' has not been declared
./Source/WebCore/platform/graphics/GraphicsLayer.h:410:45: error: 'PlatformLayer' has not been declared
./Source/WebCore/platform/graphics/GraphicsLayer.h:416:34: error: 'PlatformLayer' has not been declared
./Source/WebCore/platform/graphics/GraphicsLayer.h:419:13: error: 'PlatformLayer' does not name a type
make[1]: *** [Source/WebKit/gtk/WebCoreSupport/libwebkitgtk_3_0_la-AcceleratedCompositingContextGL.lo] Error 1
make[1]: Leaving directory `/home/administrator/src/WebKit'
make: *** [all] Error 2

does anyone have any tips or a solution for the "error: 'PlatformLayer' has not been declared" problem ?

Best regards
B.-D.

---

