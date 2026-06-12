---
title: "PIL Image Class Error on Install"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by dyanibgud on 2008-02-25
I was trying to install PIL Python Image Class to Ubuntu Linux 7.10 Gutsy and I keep getting this error while running setup.py build:

[B]running build
running build_py
running build_ext
building '_imaging' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -IlibImaging -I/usr/include -I/usr/local/include -I/usr/include/python2.4 -c _imaging.c -o build/temp.linux-i686-2.4/_imaging.o
_imaging.c:76:20: error: Python.h: No such file or directory
In file included from libImaging/Imaging.h:14,
                 from _imaging.c:78:
libImaging/ImPlatform.h:10:20: error: Python.h: No such file or directory
libImaging/ImPlatform.h:14:2: error: #error Sorry, this library requires support for ANSI prototypes.
libImaging/ImPlatform.h:17:2: error: #error Sorry, this library requires ANSI header files.
libImaging/ImPlatform.h:55:2: error: #error Cannot find required 32-bit integer type
In file included from _imaging.c:78:
libImaging/Imaging.h:90: error: expected specifier-qualifier-list before ‘INT32’
libImaging/Imaging.h:265: error: expected specifier-qualifier-list before ‘INT32’
libImaging/Imaging.h:393: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ImagingCRC32’
_imaging.c:123: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
_imaging.c:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PyTypeObject’
_imaging.c:141: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
_imaging.c:149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PyTypeObject’
_imaging.c:152: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
_imaging.c:158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PyTypeObject’
_imaging.c:163: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
_imaging.c:168: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PyTypeObject’
_imaging.c:170: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c: In function ‘_dealloc’:
_imaging.c:201: error: ‘ImagingObject’ has no member named ‘image’
_imaging.c:202: warning: implicit declaration of function ‘PyMem_DEL’
_imaging.c: At top level:
_imaging.c:207: error: expected ‘)’ before ‘*’ token
_imaging.c: In function ‘ImagingSectionEnter’:
_imaging.c:225: error: ‘PyThreadState’ undeclared (first use in this function)
_imaging.c:225: error: (Each undeclared identifier is reported only once
_imaging.c:225: error: for each function it appears in.)
_imaging.c:225: error: expected expression before ‘)’ token
_imaging.c: In function ‘ImagingSectionLeave’:
_imaging.c:232: warning: implicit declaration of function ‘PyEval_RestoreThread’
_imaging.c:232: error: ‘PyThreadState’ undeclared (first use in this function)
_imaging.c:232: error: expected expression before ‘)’ token
_imaging.c: In function ‘ImagingError_IOError’:
_imaging.c:253: warning: implicit declaration of function ‘PyErr_SetString’
_imaging.c:253: error: ‘PyExc_IOError’ undeclared (first use in this function)
_imaging.c:254: error: ‘NULL’ undeclared (first use in this function)
_imaging.c: In function ‘ImagingError_MemoryError’:
_imaging.c:260: warning: implicit declaration of function ‘PyErr_NoMemory’
_imaging.c:260: warning: return makes pointer from integer without a cast
_imaging.c: In function ‘ImagingError_Mismatch’:
_imaging.c:266: error: ‘PyExc_ValueError’ undeclared (first use in this function)
_imaging.c:267: error: ‘NULL’ undeclared (first use in this function)
_imaging.c: In function ‘ImagingError_ModeError’:
_imaging.c:273: error: ‘PyExc_ValueError’ undeclared (first use in this function)
_imaging.c:274: error: ‘NULL’ undeclared (first use in this function)
_imaging.c: In function ‘ImagingError_ValueError’:
_imaging.c:281: error: ‘PyExc_ValueError’ undeclared (first use in this function)
_imaging.c:284: error: ‘NULL’ undeclared (first use in this function)
_imaging.c: At top level:
_imaging.c:316: error: expected ‘)’ before ‘*’ token
_imaging.c:413: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:468: error: expected ‘)’ before ‘*’ token
_imaging.c:536: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:568: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:580: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:592: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:604: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:613: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:624: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:635: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:646: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:668: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:692: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:709: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:726: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:735: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:752: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:762: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:773: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:805: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:840: error: expected ‘)’ before ‘*’ token
_imaging.c:880: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:902: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:975: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:986: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:996: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1035: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1260: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1280: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1315: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1340: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1371: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1382: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1402: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1453: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1485: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1531: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1606: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1657: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1663: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1675: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1709: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1737: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1767: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1778: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1794: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1815: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1821: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1832: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1843: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1854: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1865: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1876: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1894: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1912: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1923: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1934: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1945: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1956: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:1974: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c: In function ‘_font_dealloc’:
_imaging.c:2035: warning: implicit declaration of function ‘Py_XDECREF’
_imaging.c:2035: error: ‘ImagingFontObject’ has no member named ‘ref’
_imaging.c: In function ‘textwidth’:
_imaging.c:2045: error: ‘ImagingFontObject’ has no member named ‘glyphs’
_imaging.c: At top level:
_imaging.c:2050: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2098: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2108: error: array type has incomplete element type
_imaging.c:2109: error: ‘PyCFunction’ undeclared here (not in a function)
_imaging.c:2109: error: expected ‘}’ before ‘_font_getmask’
_imaging.c:2110: error: expected ‘}’ before ‘_font_getsize’
_imaging.c:2111: error: ‘NULL’ undeclared here (not in a function)
_imaging.c:2114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c: In function ‘_draw_dealloc’:
_imaging.c:2150: error: ‘ImagingDrawObject’ has no member named ‘image’
_imaging.c: At top level:
_imaging.c:2154: error: expected ‘)’ before ‘*’ token
_imaging.c:2156: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2191: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2228: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2246: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2283: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2299: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2352: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2367: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2400: error: expected ‘)’ before ‘*’ token
_imaging.c:2402: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2447: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2493: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2530: error: array type has incomplete element type
_imaging.c:2533: error: expected ‘}’ before ‘_draw_line’
_imaging.c:2534: error: expected ‘}’ before ‘_draw_lines’
_imaging.c:2536: error: expected ‘}’ before ‘_draw_outline’
_imaging.c:2538: error: expected ‘}’ before ‘_draw_polygon’
_imaging.c:2539: error: expected ‘}’ before ‘_draw_rectangle’
_imaging.c:2540: error: expected ‘}’ before ‘_draw_point’
_imaging.c:2541: error: expected ‘}’ before ‘_draw_points’
_imaging.c:2542: error: expected ‘}’ before ‘_draw_arc’
_imaging.c:2543: error: expected ‘}’ before ‘_draw_bitmap’
_imaging.c:2544: error: expected ‘}’ before ‘_draw_chord’
_imaging.c:2545: error: expected ‘}’ before ‘_draw_ellipse’
_imaging.c:2546: error: expected ‘}’ before ‘_draw_pieslice’
_imaging.c:2547: error: expected ‘}’ before ‘_draw_ink’
_imaging.c:2552: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2561: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c: In function ‘pixel_access_dealloc’:
_imaging.c:2586: error: ‘PixelAccessObject’ has no member named ‘image’
_imaging.c: At top level:
_imaging.c:2590: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2601: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_imaging.c:2601: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_imaging.c: In function ‘pixel_access_setitem’:
_imaging.c:2603: error: ‘PixelAccessObject’ has no member named ‘image’
_imaging.c:2607: error: ‘PixelAccessObject’ has no member named ‘readonly’
_imaging.c:2612: warning: implicit declaration of function ‘_getxy’
_imaging.c:2612: error: ‘xy’ undeclared (first use in this function)
_imaging.c:2616: error: ‘PyExc_IndexError’ undeclared (first use in this function)
_imaging.c:2620: error: ‘color’ undeclared (first use in this function)
_imaging.c:2623: warning: implicit declaration of function ‘getink’
_imaging.c:2629: error: ‘struct ImagingMemoryInstance’ has no member named ‘image32’
_imaging.c:2629: error: ‘INT32’ undeclared (first use in this function)
_imaging.c:2629: error: expected expression before ‘)’ token
_imaging.c: At top level:
_imaging.c:2640: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2659: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2670: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2687: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2707: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2742: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2763: error: array type has incomplete element type
_imaging.c:2766: error: expected ‘}’ before ‘_getpixel’
_imaging.c:2767: error: expected ‘}’ before ‘_putpixel’
_imaging.c:2769: error: expected ‘}’ before ‘pixel_access_new’
_imaging.c:2772: error: expected ‘}’ before ‘_convert’
_imaging.c:2773: error: expected ‘}’ before ‘_convert2’
_imaging.c:2774: error: expected ‘}’ before ‘_convert_matrix’
_imaging.c:2775: error: expected ‘}’ before ‘_copy’
_imaging.c:2776: error: expected ‘}’ before ‘_copy2’
_imaging.c:2780: error: expected ‘}’ before ‘_crop’
_imaging.c:2781: error: expected ‘}’ before ‘_expand’
_imaging.c:2782: error: expected ‘}’ before ‘_filter’
_imaging.c:2783: error: expected ‘}’ before ‘_histogram’
_imaging.c:2785: error: expected ‘}’ before ‘_modefilter’
_imaging.c:2787: error: expected ‘}’ before ‘_offset’
_imaging.c:2788: error: expected ‘}’ before ‘_paste’
_imaging.c:2789: error: expected ‘}’ before ‘_point’
_imaging.c:2790: error: expected ‘}’ before ‘_point_transform’
_imaging.c:2791: error: expected ‘}’ before ‘_putdata’
_imaging.c:2793: error: expected ‘}’ before ‘_quantize’
_imaging.c:2796: error: expected ‘}’ before ‘_rankfilter’
_imaging.c:2798: error: expected ‘}’ before ‘_resize’
_imaging.c:2799: error: expected ‘}’ before ‘_rotate’
_imaging.c:2800: error: expected ‘}’ before ‘_stretch’
_imaging.c:2801: error: expected ‘}’ before ‘_transpose’
_imaging.c:2802: error: expected ‘}’ before ‘_transform2’
_imaging.c:2804: error: expected ‘}’ before ‘_isblock’
_imaging.c:2806: error: expected ‘}’ before ‘_getbbox’
_imaging.c:2807: error: expected ‘}’ before ‘_getcolors’
_imaging.c:2808: error: expected ‘}’ before ‘_getextrema’
_imaging.c:2809: error: expected ‘}’ before ‘_getprojection’
_imaging.c:2811: error: expected ‘}’ before ‘_getband’
_imaging.c:2812: error: expected ‘}’ before ‘_putband’
_imaging.c:2813: error: expected ‘}’ before ‘_fillband’
_imaging.c:2815: error: expected ‘}’ before ‘im_setmode’
_imaging.c:2817: error: expected ‘}’ before ‘_getpalette’
_imaging.c:2818: error: expected ‘}’ before ‘_putpalette’
_imaging.c:2819: error: expected ‘}’ before ‘_putpalettealpha’
_imaging.c:2823: error: expected ‘}’ before ‘_chop_invert’
_imaging.c:2824: error: expected ‘}’ before ‘_chop_lighter’
_imaging.c:2825: error: expected ‘}’ before ‘_chop_darker’
_imaging.c:2826: error: expected ‘}’ before ‘_chop_difference’
_imaging.c:2827: error: expected ‘}’ before ‘_chop_multiply’
_imaging.c:2828: error: expected ‘}’ before ‘_chop_screen’
_imaging.c:2829: error: expected ‘}’ before ‘_chop_add’
_imaging.c:2830: error: expected ‘}’ before ‘_chop_subtract’
_imaging.c:2831: error: expected ‘}’ before ‘_chop_add_modulo’
_imaging.c:2832: error: expected ‘}’ before ‘_chop_subtract_modulo’
_imaging.c:2833: error: expected ‘}’ before ‘_chop_and’
_imaging.c:2834: error: expected ‘}’ before ‘_chop_or’
_imaging.c:2835: error: expected ‘}’ before ‘_chop_xor’
_imaging.c:2840: error: expected ‘}’ before ‘_effect_spread’
_imaging.c:2844: error: expected ‘}’ before ‘_new_array’
_imaging.c:2845: error: expected ‘}’ before ‘_new_block’
_imaging.c:2848: error: expected ‘}’ before ‘_save_ppm’
_imaging.c:2857: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c: In function ‘image_length’:
_imaging.c:2886: error: ‘ImagingObject’ has no member named ‘image’
_imaging.c: At top level:
_imaging.c:2891: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2906: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘image_as_sequence’
_imaging.c:2919: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PyTypeObject’
_imaging.c:2940: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PyTypeObject’
_imaging.c:2952: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PyTypeObject’
_imaging.c:2966: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pixel_access_as_mapping’
_imaging.c:2974: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PyTypeObject’
_imaging.c:2996: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2997: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2998: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:2999: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3000: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3001: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3002: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3003: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3004: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3005: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3006: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3007: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3008: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3009: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3010: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3013: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3014: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3015: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3016: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3017: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3018: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3019: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3033: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3036: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3038: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3039: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_imaging.c:3041: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘functions’
_imaging.c:3138: warning: return type defaults to ‘int’
_imaging.c: In function ‘DL_EXPORT’:
_imaging.c:3138: error: expected declaration specifiers before ‘init_imaging’
_imaging.c:3149: error: expected ‘{’ at end of input
error: command 'gcc' failed with exit status 1
[/B]

What seems to be wrong? Can someone help me out?  Thanks! :(

---

### Post by dyanibgud on 2008-02-25
Anyway, I was able to figure out the solution. I needed an installation of python-dev, which I can get from Synaptic Package Manager. After installing that, everything's okay!

---

### Post by jgeewax on 2008-07-18
Thanks for this. Solved my problem!

JJG

---

