---
title: "Can't Complie XV"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by 4Play on 2007-09-23
Hello, I am running Ubuntu 7.04 and am trying to complie XV ([http://www.trilon.com/xv/downloads.html](http://www.trilon.com/xv/downloads.html)) since it is not available in the repositories...

So i get the tarball, install the build-essentials package: sudo aptitude install build-essential
but when I try to run "make" i get the following error messages:

> xv.h:1404: error: expected ')' before '*' token
xv.h:1405: warning: parameter names (without types) in function declaration
xv.h:1427: warning: parameter names (without types) in function declaration
xv.h:1429: error: expected ')' before '*' token
xv.h:1430: warning: parameter names (without types) in function declaration
xv.h:1436: error: expected ')' before '*' token
xv.h:1454: error: expected declaration specifiers or '...' before 'Window'
xv.h:1468: error: expected declaration specifiers or '...' before 'Window'
xv.h:1480: error: expected declaration specifiers or '...' before 'Window'
xv.h:1488: error: expected declaration specifiers or '...' before 'Window'
xv.h:1500: error: expected declaration specifiers or '...' before 'Window'
xv.h:1509: error: expected declaration specifiers or '...' before 'Window'
xv.h:1522: error: expected declaration specifiers or '...' before 'Window'
xv.h:1527: error: expected declaration specifiers or '...' before 'Window'
xv.h:1606: error: expected ')' before '*' token
xv.h:1613: error: expected ')' before '*' token
xv.h:1622: error: expected ')' before '*' token
xv.h:1628: error: expected ')' before 'int'
xv.h:1638: error: expected ')' before '*' token
xv.h:1639: error: expected ')' before 'char'
xv.h:1667: error: expected ')' before '*' token
xv.c:61: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__SWM_VROOT'
xv.c:91: error: expected ')' before '*' token
xv.c: In function 'main':
xv.c:140: error: 'XColor' undeclared (first use in this function)
xv.c:140: error: (Each undeclared identifier is reported only once
xv.c:140: error: for each function it appears in.)
xv.c:140: error: expected ';' before 'ecdef'
xv.c:141: error: 'Window' undeclared (first use in this function)
xv.c:141: error: expected ';' before 'rootReturn'
xv.c:171: error: 'theImage' undeclared (first use in this function)
xv.c:178: error: 'LocalCmap' undeclared (first use in this function)
xv.c:178: error: 'browCmap' undeclared (first use in this function)
xv.c:197: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:221: warning: incompatible implicit declaration of built-in function 'rindex'
xv.c:227: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:247: error: 'XC_top_left_arrow' undeclared (first use in this function)
xv.c:269: error: 'mainW' undeclared (first use in this function)
xv.c:269: error: 'dirW' undeclared (first use in this function)
xv.c:269: error: 'infoW' undeclared (first use in this function)
xv.c:269: error: 'ctrlW' undeclared (first use in this function)
xv.c:269: error: 'gamW' undeclared (first use in this function)
xv.c:269: error: 'psW' undeclared (first use in this function)
xv.c:273: error: 'jpegW' undeclared (first use in this function)
xv.c:310: error: 'theDisp' undeclared (first use in this function)
xv.c:311: error: 'theCmap' undeclared (first use in this function)
xv.c:312: error: 'rootW' undeclared (first use in this function)
xv.c:313: error: 'theGC' undeclared (first use in this function)
xv.c:314: error: 'theVisual' undeclared (first use in this function)
xv.c:335: error: 'XVisualInfo' undeclared (first use in this function)
xv.c:335: error: 'vinfo' undeclared (first use in this function)
xv.c:335: error: 'rvinfo' undeclared (first use in this function)
xv.c:340: error: 'TrueColor' undeclared (first use in this function)
xv.c:342: error: 'VisualClassMask' undeclared (first use in this function)
xv.c:342: error: 'VisualScreenMask' undeclared (first use in this function)
xv.c:353: error: 'DirectColor' undeclared (first use in this function)
xv.c:381: error: 'StaticGray' undeclared (first use in this function)
xv.c:382: error: 'StaticColor' undeclared (first use in this function)
xv.c:384: error: 'GrayScale' undeclared (first use in this function)
xv.c:385: error: 'PseudoColor' undeclared (first use in this function)
xv.c:407: error: 'VisualIDMask' undeclared (first use in this function)
xv.c:438: error: 'XGCValues' undeclared (first use in this function)
xv.c:438: error: expected ';' before 'xgcv'
xv.c:439: error: 'xgcv' undeclared (first use in this function)
xv.c:439: error: 'False' undeclared (first use in this function)
xv.c:440: error: 'GCGraphicsExposures' undeclared (first use in this function)
xv.c:447: error: 'xvErrorHandler' undeclared (first use in this function)
xv.c:450: error: 'vrootW' undeclared (first use in this function)
xv.c:452: error: '__SWM_VROOT' undeclared (first use in this function)
xv.c:453: error: 'rootReturn' undeclared (first use in this function)
xv.c:453: error: 'parentReturn' undeclared (first use in this function)
xv.c:453: error: 'children' undeclared (first use in this function)
xv.c:456: error: 'Atom' undeclared (first use in this function)
xv.c:456: error: expected ';' before 'actual_type'
xv.c:459: error: 'newRoot' undeclared (first use in this function)
xv.c:460: error: 'XWindowAttributes' undeclared (first use in this function)
xv.c:460: error: expected ';' before 'xwa'
xv.c:462: error: 'XA_WINDOW' undeclared (first use in this function)
xv.c:462: error: 'actual_type' undeclared (first use in this function)
xv.c:463: error: 'Success' undeclared (first use in this function)
xv.c:465: error: 'xwa' undeclared (first use in this function)
xv.c:486: error: 'arrow' undeclared (first use in this function)
xv.c:487: error: 'cross' undeclared (first use in this function)
xv.c:487: error: 'XC_crosshair' undeclared (first use in this function)
xv.c:488: error: 'tcross' undeclared (first use in this function)
xv.c:488: error: 'XC_tcross' undeclared (first use in this function)
xv.c:489: error: 'zoom' undeclared (first use in this function)
xv.c:489: error: 'XC_sizing' undeclared (first use in this function)
xv.c:492: error: expected ';' before 'fc'
xv.c:493: error: 'fc' undeclared (first use in this function)
xv.c:494: error: 'bc' undeclared (first use in this function)
xv.c:500: error: 'Pixmap' undeclared (first use in this function)
xv.c:500: error: expected ';' before 'pix'
xv.c:502: error: expected ';' before 'cfg'
xv.c:504: error: 'cfg' undeclared (first use in this function)
xv.c:505: error: 'pix' undeclared (first use in this function)
xv.c:506: error: 'inviso' undeclared (first use in this function)
xv.c:520: error: 'ecdef' undeclared (first use in this function)
xv.c:520: error: 'DoRed' undeclared (first use in this function)
xv.c:520: error: 'DoGreen' undeclared (first use in this function)
xv.c:520: error: 'DoBlue' undeclared (first use in this function)
xv.c:596: error: 'iconPix' undeclared (first use in this function)
xv.c:597: error: 'iconmask' undeclared (first use in this function)
xv.c:598: error: 'riconPix' undeclared (first use in this function)
xv.c:599: error: 'riconmask' undeclared (first use in this function)
xv.c:604: error: 'gray50Tile' undeclared (first use in this function)
xv.c:610: error: 'gray25Tile' undeclared (first use in this function)
xv.c:618: error: 'mfinfo' undeclared (first use in this function)
xv.c:628: error: 'mfont' undeclared (first use in this function)
xv.c:631: error: 'monofinfo' undeclared (first use in this function)
xv.c:631: error: 'XFontStruct' undeclared (first use in this function)
xv.c:631: error: expected expression before ')' token
xv.c:651: error: 'monofont' undeclared (first use in this function)
xv.c:675: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:694: error: 'ExposureMask' undeclared (first use in this function)
xv.c:694: error: 'ButtonPressMask' undeclared (first use in this function)
xv.c:694: error: 'KeyPressMask' undeclared (first use in this function)
xv.c:695: error: 'StructureNotifyMask' undeclared (first use in this function)
xv.c:710: error: 'XWMHints' undeclared (first use in this function)
xv.c:710: error: expected ';' before 'xwmh'
xv.c:711: error: 'xwmh' undeclared (first use in this function)
xv.c:711: error: 'True' undeclared (first use in this function)
xv.c:712: error: 'IconicState' undeclared (first use in this function)
xv.c:713: error: 'InputHint' undeclared (first use in this function)
xv.c:713: error: 'StateHint' undeclared (first use in this function)
xv.c:728: error: 'MBUTT' has no member named 'dim'
xv.c:735: error: 'CBUTT' has no member named 'val'
xv.c:736: error: 'CBUTT' has no member named 'val'
xv.c:746: error: 'ColormapChangeMask' undeclared (first use in this function)
xv.c:761: error: 'MBUTT' has no member named 'dim'
xv.c:771: error: 'CBUTT' has no member named 'val'
xv.c:772: error: 'CBUTT' has no member named 'val'
xv.c:796: error: 'MBUTT' has no member named 'flags'
xv.c:797: error: 'MBUTT' has no member named 'dim'
xv.c:803: error: 'MBUTT' has no member named 'flags'
xv.c:808: error: 'MBUTT' has no member named 'flags'
xv.c: In function 'makeDirectCmap':
xv.c:837: error: 'XColor' undeclared (first use in this function)
xv.c:837: error: expected ';' before 'c'
xv.c:842: error: 'theVisual' undeclared (first use in this function)
xv.c:871: error: 'c' undeclared (first use in this function)
xv.c:875: error: 'DoRed' undeclared (first use in this function)
xv.c:875: error: 'DoGreen' undeclared (first use in this function)
xv.c:875: error: 'DoBlue' undeclared (first use in this function)
xv.c:877: error: 'theDisp' undeclared (first use in this function)
xv.c:877: error: 'theCmap' undeclared (first use in this function)
xv.c: At top level:
xv.c:924: warning: conflicting types for 'useOtherVisual'
xv.c:924: error: static declaration of 'useOtherVisual' follows non-static declaration
xv.c:364: error: previous implicit declaration of 'useOtherVisual' was here
xv.c: In function 'useOtherVisual':
xv.c:924: error: expected declaration specifiers before 'XVisualInfo'
xv.c:929: error: subscripted value is neither array nor pointer
xv.c:930: error: 'theDisp' undeclared (first use in this function)
xv.c:932: error: 'theVisual' undeclared (first use in this function)
xv.c:932: error: subscripted value is neither array nor pointer
xv.c:937: error: subscripted value is neither array nor pointer
xv.c:937: error: 'StaticGray' undeclared (first use in this function)
xv.c:938: error: subscripted value is neither array nor pointer
xv.c:938: error: 'StaticColor' undeclared (first use in this function)
xv.c:939: error: subscripted value is neither array nor pointer
xv.c:939: error: 'TrueColor' undeclared (first use in this function)
xv.c:940: error: subscripted value is neither array nor pointer
xv.c:940: error: 'GrayScale' undeclared (first use in this function)
xv.c:941: error: subscripted value is neither array nor pointer
xv.c:941: error: 'PseudoColor' undeclared (first use in this function)
xv.c:942: error: subscripted value is neither array nor pointer
xv.c:942: error: 'DirectColor' undeclared (first use in this function)
xv.c:943: error: subscripted value is neither array nor pointer
xv.c:944: error: subscripted value is neither array nor pointer
xv.c:944: error: subscripted value is neither array nor pointer
xv.c:947: error: subscripted value is neither array nor pointer
xv.c:947: error: subscripted value is neither array nor pointer
xv.c:948: error: subscripted value is neither array nor pointer
xv.c:948: error: subscripted value is neither array nor pointer
xv.c:951: error: subscripted value is neither array nor pointer
xv.c:952: error: subscripted value is neither array nor pointer
xv.c:953: error: 'rootW' undeclared (first use in this function)
xv.c:954: error: subscripted value is neither array nor pointer
xv.c:955: error: 'theCmap' undeclared (first use in this function)
xv.c:955: error: 'AllocNone' undeclared (first use in this function)
xv.c:961: error: 'Window' undeclared (first use in this function)
xv.c:961: error: expected ';' before 'win'
xv.c:962: error: 'XSetWindowAttributes' undeclared (first use in this function)
xv.c:962: error: expected ';' before 'xswa'
xv.c:963: error: 'XGCValues' undeclared (first use in this function)
xv.c:963: error: expected ';' before 'xgcv'
xv.c:967: error: 'False' undeclared (first use in this function)
xv.c:969: error: 'xswa' undeclared (first use in this function)
xv.c:972: error: 'CWBackPixel' undeclared (first use in this function)
xv.c:972: error: 'CWBorderPixel' undeclared (first use in this function)
xv.c:972: error: 'CWColormap' undeclared (first use in this function)
xv.c:974: error: 'win' undeclared (first use in this function)
xv.c:975: error: 'InputOutput' undeclared (first use in this function)
xv.c:980: error: 'theGC' undeclared (first use in this function)
xv.c:980: error: 'xgcv' undeclared (first use in this function)
xv.c: In function 'parseResources':
xv.c:1027: error: 'theDisp' undeclared (first use in this function)
xv.c:1075: warning: incompatible implicit declaration of built-in function 'index'
xv.c:1111: warning: incompatible implicit declaration of built-in function 'strncpy'
xv.c:1123: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c: In function 'parseCmdLine':
xv.c:1251: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:1267: warning: incompatible implicit declaration of built-in function 'index'
xv.c: In function 'verifyArgs':
xv.c:1455: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:1474: error: 'theDisp' undeclared (first use in this function)
xv.c:1474: error: 'True' undeclared (first use in this function)
xv.c: In function 'printoption':
xv.c:1534: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c: In function 'argcmp':
xv.c:1689: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c: In function 'openPic':
xv.c:1751: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:1759: error: 'theDisp' undeclared (first use in this function)
xv.c:1807: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:1834: error: 'LIST' has no member named 'selected'
xv.c:1838: error: 'LIST' has no member named 'nstr'
xv.c:1840: error: 'LIST' has no member named 'selected'
xv.c:1853: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:1861: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:2097: error: 'MBUTT' has no member named 'flags'
xv.c:2145: error: 'mainW' undeclared (first use in this function)
xv.c:2147: error: 'ExposureMask' undeclared (first use in this function)
xv.c:2147: error: 'KeyPressMask' undeclared (first use in this function)
xv.c:2148: error: 'StructureNotifyMask' undeclared (first use in this function)
xv.c:2149: error: 'ButtonPressMask' undeclared (first use in this function)
xv.c:2149: error: 'KeyReleaseMask' undeclared (first use in this function)
xv.c:2150: error: 'EnterWindowMask' undeclared (first use in this function)
xv.c:2150: error: 'LeaveWindowMask' undeclared (first use in this function)
xv.c:2190: error: 'CBUTT' has no member named 'val'
xv.c:2322: error: 'WidthValue' undeclared (first use in this function)
xv.c:2323: error: 'HeightValue' undeclared (first use in this function)
xv.c:2435: error: 'theVisual' undeclared (first use in this function)
xv.c:2435: error: 'PseudoColor' undeclared (first use in this function)
xv.c:2435: error: 'GrayScale' undeclared (first use in this function)
xv.c:2439: error: 'True' undeclared (first use in this function)
xv.c:2444: error: 'vrootW' undeclared (first use in this function)
xv.c:2462: error: 'LocalCmap' undeclared (first use in this function)
xv.c:2463: error: 'XSetWindowAttributes' undeclared (first use in this function)
xv.c:2463: error: expected ';' before 'xswa'
xv.c:2464: error: 'xswa' undeclared (first use in this function)
xv.c:2467: error: 'CWColormap' undeclared (first use in this function)
xv.c:2468: error: 'gamW' undeclared (first use in this function)
xv.c:2511: error: 'LIST' has no member named 'nstr'
xv.c: In function 'UncompressFile':
xv.c:2706: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:2709: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:2710: warning: incompatible implicit declaration of built-in function 'strcat'
xv.c: In function 'KillPageFiles':
xv.c:2786: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c: In function 'readpipe':
xv.c:2899: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:2910: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:2911: warning: incompatible implicit declaration of built-in function 'strcat'
xv.c: In function 'openNextPic':
xv.c:2973: error: 'LIST' has no member named 'selected'
xv.c:2973: error: 'LIST' has no member named 'selected'
xv.c:2974: error: 'LIST' has no member named 'selected'
xv.c: In function 'openNextQuit':
xv.c:2992: error: 'LIST' has no member named 'selected'
xv.c:2992: error: 'LIST' has no member named 'selected'
xv.c:2993: error: 'LIST' has no member named 'selected'
xv.c: In function 'openNextLoop':
xv.c:3018: error: 'LIST' has no member named 'selected'
xv.c:3018: error: 'LIST' has no member named 'selected'
xv.c:3019: error: 'LIST' has no member named 'selected'
xv.c: In function 'openPrevPic':
xv.c:3047: error: 'LIST' has no member named 'selected'
xv.c:3047: error: 'LIST' has no member named 'selected'
xv.c:3048: error: 'LIST' has no member named 'selected'
xv.c: In function 'findRandomPic':
xv.c:3102: error: 'TRUE' undeclared (first use in this function)
xv.c: In function 'mainLoop':
xv.c:3124: error: 'mainW' undeclared (first use in this function)
xv.c:3136: error: 'LIST' has no member named 'selected'
xv.c:3147: error: 'struct <anonymous>' has no member named 'active'
xv.c:3154: error: 'LIST' has no member named 'selected'
xv.c: In function 'createMainWindow':
xv.c:3174: error: 'XSetWindowAttributes' undeclared (first use in this function)
xv.c:3174: error: expected ';' before 'xswa'
xv.c:3176: error: 'XWindowAttributes' undeclared (first use in this function)
xv.c:3176: error: expected ';' before 'xwa'
xv.c:3177: error: 'XWMHints' undeclared (first use in this function)
xv.c:3177: error: expected ';' before 'xwmh'
xv.c:3178: error: 'XSizeHints' undeclared (first use in this function)
xv.c:3178: error: expected ';' before 'hints'
xv.c:3179: error: 'XClassHint' undeclared (first use in this function)
xv.c:3179: error: expected ';' before 'classh'
xv.c:3197: error: 'hints' undeclared (first use in this function)
xv.c:3198: error: 'XValue' undeclared (first use in this function)
xv.c:3198: error: 'YValue' undeclared (first use in this function)
xv.c:3198: error: 'USPosition' undeclared (first use in this function)
xv.c:3200: error: 'XNegative' undeclared (first use in this function)
xv.c:3201: error: 'YNegative' undeclared (first use in this function)
xv.c:3209: error: 'vrootW' undeclared (first use in this function)
xv.c:3209: error: 'rootW' undeclared (first use in this function)
xv.c:3211: error: 'Window' undeclared (first use in this function)
xv.c:3211: error: expected ';' before 'child'
xv.c:3212: error: 'theDisp' undeclared (first use in this function)
xv.c:3212: error: 'child' undeclared (first use in this function)
xv.c:3221: error: 'USSize' undeclared (first use in this function)
xv.c:3221: error: 'PMaxSize' undeclared (first use in this function)
xv.c:3223: error: 'xswa' undeclared (first use in this function)
xv.c:3223: error: 'StaticGravity' undeclared (first use in this function)
xv.c:3226: error: 'theCmap' undeclared (first use in this function)
xv.c:3228: error: 'WhenMapped' undeclared (first use in this function)
xv.c:3239: error: 'CWBackPixel' undeclared (first use in this function)
xv.c:3239: error: 'CWBorderPixel' undeclared (first use in this function)
xv.c:3239: error: 'CWColormap' undeclared (first use in this function)
xv.c:3240: error: 'CWBitGravity' undeclared (first use in this function)
xv.c:3242: error: 'mainW' undeclared (first use in this function)
xv.c:3243: error: 'xwa' undeclared (first use in this function)
xv.c:3253: error: 'PSize' undeclared (first use in this function)
xv.c:3258: error: 'InputOutput' undeclared (first use in this function)
xv.c:3259: error: 'theVisual' undeclared (first use in this function)
xv.c:3264: error: 'LocalCmap' undeclared (first use in this function)
xv.c:3271: error: 'None' undeclared (first use in this function)
xv.c:3274: error: 'xwmh' undeclared (first use in this function)
xv.c:3274: error: 'True' undeclared (first use in this function)
xv.c:3275: error: 'InputHint' undeclared (first use in this function)
xv.c:3277: error: 'iconPix' undeclared (first use in this function)
xv.c:3278: error: 'iconmask' undeclared (first use in this function)
xv.c:3279: error: 'IconPixmapHint' undeclared (first use in this function)
xv.c:3279: error: 'IconMaskHint' undeclared (first use in this function)
xv.c:3283: error: 'IconicState' undeclared (first use in this function)
xv.c:3284: error: 'StateHint' undeclared (first use in this function)
xv.c:3294: error: 'IconPositionHint' undeclared (first use in this function)
xv.c:3300: error: 'classh' undeclared (first use in this function)
xv.c:3306: error: 'Atom' undeclared (first use in this function)
xv.c:3306: error: expected ';' before 'mwm_wm_hints'
xv.c:3315: error: 'mwm_wm_hints' undeclared (first use in this function)
xv.c:3315: error: 'False' undeclared (first use in this function)
xv.c:3322: error: 'PropModeReplace' undeclared (first use in this function)
xv.c: In function 'setWinIconNames':
xv.c:3340: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:3353: warning: incompatible implicit declaration of built-in function 'strcat'
xv.c:3356: error: 'mainW' undeclared (first use in this function)
xv.c:3357: error: 'theDisp' undeclared (first use in this function)
xv.c: In function 'makeDispNames':
xv.c:3429: warning: incompatible implicit declaration of built-in function 'index'
xv.c: In function 'fixDispNames':
xv.c:3458: error: 'LIST' has no member named 'w'
xv.c:3461: warning: incompatible implicit declaration of built-in function 'index'
xv.c:3465: error: 'LIST' has no member named 'w'
xv.c: In function 'StickInCtrlList':
xv.c:3491: error: 'LIST' has no member named 'selected'
xv.c: In function 'AddFNameToCtrlList':
xv.c:3516: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:3522: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:3525: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:3525: warning: incompatible implicit declaration of built-in function 'strcat'
xv.c:3533: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:3535: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c: In function 'ChangedCtrlList':
xv.c:3562: error: 'MBUTT' has no member named 'dim'
xv.c:3564: error: 'LIST' has no member named 'selected'
xv.c:3566: error: 'LIST' has no member named 'selected'
xv.c: In function 'ActivePrevNext':
xv.c:3587: error: 'LIST' has no member named 'selected'
xv.c: In function 'DeleteCmd':
xv.c:3610: error: 'LIST' has no member named 'selected'
xv.c:3625: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:3647: error: 'LIST' has no member named 'selected'
xv.c: In function 'deleteFromList':
xv.c:3681: error: 'MBUTT' has no member named 'dim'
xv.c:3683: error: 'LIST' has no member named 'nstr'
xv.c:3684: error: 'LIST' has no member named 'selected'
xv.c:3686: error: 'LIST' has no member named 'selected'
xv.c:3686: error: 'LIST' has no member named 'selected'
xv.c:3687: error: 'LIST' has no member named 'selected'
xv.c:3687: error: 'LIST' has no member named 'selected'
xv.c:3689: error: 'LIST' has no member named 'scrl'
xv.c:3689: error: 'LIST' has no member named 'nlines'
xv.c:3690: error: 'LIST' has no member named 'scrl'
xv.c:3690: error: 'LIST' has no member named 'nlines'
xv.c: In function 'HandleDispMode':
xv.c:3707: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'oldMainW'
xv.c:3707: error: 'oldMainW' undeclared (first use in this function)
xv.c:3709: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'oldHints'
xv.c:3709: error: 'oldHints' undeclared (first use in this function)
xv.c:3710: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'oldXwa'
xv.c:3710: error: 'oldXwa' undeclared (first use in this function)
xv.c:3735: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:3742: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:3748: warning: incompatible implicit declaration of built-in function 'strcat'
xv.c:3755: error: 'mainW' undeclared (first use in this function)
xv.c:3755: error: 'Window' undeclared (first use in this function)
xv.c:3759: error: 'XWMHints' undeclared (first use in this function)
xv.c:3759: error: expected ';' before 'xwmh'
xv.c:3764: error: 'MBUTT' has no member named 'dim'
xv.c:3765: error: 'MBUTT' has no member named 'dim'
xv.c:3767: error: 'theDisp' undeclared (first use in this function)
xv.c:3767: error: 'None' undeclared (first use in this function)
xv.c:3770: error: 'xwmh' undeclared (first use in this function)
xv.c:3770: error: 'NormalState' undeclared (first use in this function)
xv.c:3771: error: 'True' undeclared (first use in this function)
xv.c:3772: error: 'InputHint' undeclared (first use in this function)
xv.c:3774: error: 'iconPix' undeclared (first use in this function)
xv.c:3775: error: 'iconmask' undeclared (first use in this function)
xv.c:3776: error: 'IconPixmapHint' undeclared (first use in this function)
xv.c:3776: error: 'IconMaskHint' undeclared (first use in this function)
xv.c:3778: error: 'StateHint' undeclared (first use in this function)
xv.c:3790: error: 'ExposureMask' undeclared (first use in this function)
xv.c:3790: error: 'KeyPressMask' undeclared (first use in this function)
xv.c:3791: error: 'StructureNotifyMask' undeclared (first use in this function)
xv.c:3791: error: 'ButtonPressMask' undeclared (first use in this function)
xv.c:3792: error: 'KeyReleaseMask' undeclared (first use in this function)
xv.c:3792: error: 'ColormapChangeMask' undeclared (first use in this function)
xv.c:3793: error: 'EnterWindowMask' undeclared (first use in this function)
xv.c:3793: error: 'LeaveWindowMask' undeclared (first use in this function)
xv.c:3810: error: 'LocalCmap' undeclared (first use in this function)
xv.c:3833: error: 'MBUTT' has no member named 'dim'
xv.c:3834: error: 'MBUTT' has no member named 'dim'
xv.c:3843: error: 'USPosition' undeclared (first use in this function)
xv.c:3853: error: 'vrootW' undeclared (first use in this function)
xv.c:3856: error: expected ';' before 'xwmh'
xv.c:3858: error: 'IconicState' undeclared (first use in this function)
xv.c:3860: error: 'ctrlW' undeclared (first use in this function)
xv.c: In function 'add_filelist_to_namelist':
xv.c:3915: warning: incompatible implicit declaration of built-in function 'strlen'
xv.c:3917: warning: incompatible implicit declaration of built-in function 'rindex'
xv.c:3919: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c: In function 'rd_flag':
xv.c:3983: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c: In function 'rd_str_cl':
xv.c:4013: error: 'XrmValue' undeclared (first use in this function)
xv.c:4013: error: expected ';' before 'result'
xv.c:4015: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'def_resource'
xv.c:4015: error: 'def_resource' undeclared (first use in this function)
xv.c:4026: error: 'Atom' undeclared (first use in this function)
xv.c:4026: error: expected ';' before 'resAtom'
xv.c:4031: error: 'XrmDatabase' undeclared (first use in this function)
xv.c:4031: error: expected ';' before numeric constant
xv.c:4039: error: 'resAtom' undeclared (first use in this function)
xv.c:4039: error: 'theDisp' undeclared (first use in this function)
xv.c:4039: error: 'True' undeclared (first use in this function)
xv.c:4040: error: 'None' undeclared (first use in this function)
xv.c:4041: error: expected ';' before 'actType'
xv.c:4047: error: 'False' undeclared (first use in this function)
xv.c:4048: error: 'XA_STRING' undeclared (first use in this function)
xv.c:4048: error: 'actType' undeclared (first use in this function)
xv.c:4050: error: 'Success' undeclared (first use in this function)
xv.c:4067: warning: assignment makes pointer from integer without a cast
xv.c:4075: error: expected ';' before 'res1'
xv.c:4097: error: 'res1' undeclared (first use in this function)
xv.c:4120: warning: incompatible implicit declaration of built-in function 'strcpy'
xv.c:4121: warning: incompatible implicit declaration of built-in function 'strcat'
xv.c:4128: error: 'result' undeclared (first use in this function)
make: *** [xv.o] Error 1


this is just the part that shows in the terminal....

I have researched a bit and have seen suggestions that this problem has something to do with the kernel....

There is no configure file in the main folder, but i ran ./configure in the "jpeg" subfolder and everything checked out ok

Anyway, this is probably quite simple, it's just that I'm not really used to compiling stuff, as there is usually a .deb package available

Thanks 4 any help :)

---

### Post by yabbadabbadont on 2007-09-23
xv hasn't been updated for more than 10 years.  Most distributions don't include it any more for that reason and also because it is shareware.  However, I found a site that has user contributed patches and compiling instructions, including the dependencies (which you are probably missing), here:
[http://www.sonic.net/~roelofs/greg_xv.html](http://www.sonic.net/~roelofs/greg_xv.html)

Good luck.

---

