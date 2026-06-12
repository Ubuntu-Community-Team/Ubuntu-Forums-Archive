---
title: "Help with script"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Steve H on 2008-11-29
I'm using WINE (1.1.9) to run [The Many Faces Of Go]("http://www.smart-games.com/manyfaces.html"), and its running fine except for the graphics have a problem with transparency. Anyway I've found this script which says it will fix the problem, (but I don't know how to run it):
```
diff --git a/dlls/winex11.drv/palette.c b/dlls/winex11.drv/palette.c
index bb6d493..8039bf3 100644
--- a/dlls/winex11.drv/palette.c
+++ b/dlls/winex11.drv/palette.c
@@ -48,6 +48,9 @@ WINE_DEFAULT_DEBUG_CHANNEL(palette);
  * http://premium.microsoft.com/msdn/library/techart/f30/f34/f40/d4d/sa942.htm
  */

+#undef MIN
+#define MIN(x, y) ( ((x)<(y))?(x):(y) )
+
 #define NB_RESERVED_COLORS     20   /* number of fixed colors in system palette */

 #define PC_SYS_USED            0x80 /* palentry is used (both system and logical) */
@@ -1223,6 +1226,37 @@ UINT X11DRV_GetSystemPaletteEntries( X11DRV_PDEVICE *physDev, UINT start,
UINT c
 {
     UINT i;

+    /*in non-palette mode report palette size of 256 and set reserved colors*/
+    if (X11DRV_PALETTE_PaletteFlags & X11DRV_PALETTE_VIRTUAL)
+    {
+        if (!entries) return 256;
+
+        if (start >= 256) return 0;
+        if (start + count >= 256) count = 256 - start;
+
+        if (start < NB_RESERVED_COLORS/2)
+        {
+            GetPaletteEntries( GetStockObject(DEFAULT_PALETTE), start,
+                MIN(NB_RESERVED_COLORS/2 - start, count), entries);
+        }
+
+        if (start >= 256 - NB_RESERVED_COLORS/2)
+        {
+            GetPaletteEntries( GetStockObject(DEFAULT_PALETTE),
+                NB_RESERVED_COLORS/2 + start - (256 - NB_RESERVED_COLORS/2),
+                count, entries);
+        }
+        else if (start + count > 256 - NB_RESERVED_COLORS/2)
+        {
+            GetPaletteEntries( GetStockObject(DEFAULT_PALETTE),
+                NB_RESERVED_COLORS/2,
+                start + count - (256 - NB_RESERVED_COLORS/2),
+                entries + (256 - NB_RESERVED_COLORS/2) - start);
+        }
+
+        return count;
+    }
+
     if (!entries) return palette_size;
     if (start >= palette_size) return 0;
     if (start + count >= palette_size) count = palette_size - start;


diff --git a/dlls/gdi32/tests/palette.c b/dlls/gdi32/tests/palette.c
index 40e6c7c..15fba1a 100644
--- a/dlls/gdi32/tests/palette.c
+++ b/dlls/gdi32/tests/palette.c
@@ -40,6 +40,31 @@ static const PALETTEENTRY logpalettedata[8] = {
     { 0x80, 0x90, 0xA0, PC_NOCOLLAPSE },
 };

+static const PALETTEENTRY static_colors[20] = {
+/* 0..9 */
+    { 0x00, 0x00, 0x00, 0 },
+    { 0x80, 0x00, 0x00, 0 },
+    { 0x00, 0x80, 0x00, 0 },
+    { 0x80, 0x80, 0x00, 0 },
+    { 0x00, 0x00, 0x80, 0 },
+    { 0x80, 0x00, 0x80, 0 },
+    { 0x00, 0x80, 0x80, 0 },
+    { 0xC0, 0xC0, 0xC0, 0 },
+    { 0xC0, 0xDC, 0xC0, 0 },
+    { 0xA6, 0xCA, 0xF0, 0 },
+/* 246..255 */
+    { 0xFF, 0xFB, 0xF0, 0 },
+    { 0xA0, 0xA0, 0xA4, 0 },
+    { 0x80, 0x80, 0x80, 0 },
+    { 0xFF, 0x00, 0x00, 0 },
+    { 0x00, 0xFF, 0x00, 0 },
+    { 0xFF, 0xFF, 0x00, 0 },
+    { 0x00, 0x00, 0xFF, 0 },
+    { 0xFF, 0x00, 0xFF, 0 },
+    { 0x00, 0xFF, 0xFF, 0 },
+    { 0xFF, 0xFF, 0xFF, 0 }
+    };
+
 static void test_DIB_PAL_COLORS(void) {
     HDC hdc = GetDC( NULL );
     HDC memhdc = CreateCompatibleDC( hdc );
@@ -51,6 +76,8 @@ static void test_DIB_PAL_COLORS(void) {
     PLOGPALETTE logpalette = (PLOGPALETTE)logpalettebuf;
     HPALETTE hpal, hpalOld;
     COLORREF setColor, chkColor, getColor;
+    UINT nentries;
+    PALETTEENTRY syspalentries[256];
     int i;

     /* Initalize the logical palette with a few colours */
@@ -117,6 +144,27 @@ static void test_DIB_PAL_COLORS(void) {
     SelectObject( memhdc, hbmpOld );
     DeleteObject( hbmp );
     DeleteDC( memhdc );
+
+    memset(syspalentries, 0x01, sizeof(syspalentries));
+    SetLastError(0);
+    nentries = GetSystemPaletteEntries(hdc, 0, 256, syspalentries);
+    /* According to MSDN, it is supposed to return number of copied
+       entries and zero return value indicates a failure; On Windows XP it
+       always returns 0, although it does fill entries; On Windows 98 it
+       correctly returns 256 in most graphics modes; It can also return 16 on
+       W98 - when called in 16 color / VGA mode */
+    ok( (nentries == 0 || nentries == 256 || nentries == 16) && GetLastError()==0,
+        "nentries=%u error=%d\n", nentries, GetLastError());
+    if (nentries == 16) skip("will not check reserved colors (VGA mode?)\n");
+    else {
+        /* Test if 20 static(reserved) colors are present */
+        ok( !memcmp(static_colors, syspalentries, sizeof(PALETTEENTRY) * 10),
+            "system palette low 10 static colors are wrong\n");
+        ok( !memcmp(static_colors + 10, syspalentries + 256 - 10,
+            sizeof(PALETTEENTRY) *10),
+            "system palette high 10 static colors are wrong\n");
+    }
+
     ReleaseDC( NULL, hdc );
 }
```


Anyone got any ideas how I'm supoosed to use this??

The website I found it on is [here]("http://article.gmane.org/gmane.comp.emulators.wine.devel/54403)")

---

