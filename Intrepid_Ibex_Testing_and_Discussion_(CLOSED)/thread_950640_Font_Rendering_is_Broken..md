---
title: "Font Rendering is Broken."
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by theBishop on 2008-10-17
Part of my job is doing graphic design.  So I was installing some new fonts in the Intrepid beta, and realized the font rendering is busted.  After trying a few different Application fonts, I went back to the default Sans (10pt, regular).  But now, there's a lot of problems.  For one thing, the numbers don't seem to be 100% Sans anymore.  Take a look:

[img]http://i37.tinypic.com/30mr3mu.jpg[/img]

And here are the numbers up close:
[img]http://i33.tinypic.com/2s6kk8m.png[/img]

These are two different applications that should both be using the same font.  But you can see, the bottom is what Sans is *supposed* to look like, and the top is something else.  The 2's, 3's, and 7's are especially noticeable.  You can see how the characters on the top "hook", while the bottom characters are more straight.

And it gets worse.  The must be an inconsistency in size or pixel resolution or something, because characters are disappearing or shifting in some applications.

Take a look at Xchat:
[img]http://i34.tinypic.com/123m9l1.png[/img]

I've highlighted in red where the text is behind randomly cut off, and in blue where you can see the numbers are obviously not the same font as the letters.  I also highlighted in green where the correct font is being applied to numbers in the user list.  

Now when I highlight text, some characters disappear and others appear:
[img]http://i38.tinypic.com/2ppem2q.png[/img]

Here's another screen that I think shows clearly that the numbers are not the same font as the letters.  This is from the file selection window:
[img]http://i36.tinypic.com/2ikbd78.png[/img]

Is anyone else having this problem?  Even as I type in this text window (Firefox), I can see characters shifting subtly.  Whether it's spacing between characters or between lines, it's small but distracting.  This makes using Ubuntu for work impossible for me.

---

### Post by kj74 on 2008-10-17
First thing to do is log out and log in again, if you haven't done it already.

Sans is just alias for DejaVu(i think) fonts, select those instead of sans. If you use lcd sub-pixel rendering, make sure you have full hinting enabled.

---

### Post by theBishop on 2008-10-20
> **kj74 said:**
> First thing to do is log out and log in again, if you haven't done it already.

Sans is just alias for DejaVu(i think) fonts, select those instead of sans. If you use lcd sub-pixel rendering, make sure you have full hinting enabled.

I've logged in/out several times.  It's been like this for a few days now.

---

### Post by theBishop on 2008-10-20
It also may be causing instability in Firefox.  Firefox has been miserably unstable for me, crashing constantly without warning.  I've started running it from a terminal so I can capture the error output.  Here's the output from my most recent crash:
```

*** glibc detected *** /usr/lib/firefox-3.0.3/firefox: realloc(): invalid next size: 0x0b3010c8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d2a3f4]
/lib/tls/i686/cmov/libc.so.6[0xb7d2e051]
/lib/tls/i686/cmov/libc.so.6(realloc+0x106)[0xb7d2ed86]
/usr/lib/libglib-2.0.so.0(g_realloc+0x3a)[0xb6b4ec4a]
/usr/lib/libpango-1.0.so.0(pango_glyph_string_set_size+0xb1)[0xb6cb65b1]
/usr/lib/pango/1.6.0/modules/pango-basic-fc.so[0xb3a7ee3e]
/usr/lib/libpango-1.0.so.0[0xb6cbcfaa]
/usr/lib/libpango-1.0.so.0(pango_shape+0x5a)[0xb6cd030a]
/usr/lib/xulrunner-1.9.0.3/libxul.so(_ZN17gfxPangoFontGroup24CreateGlyphRunsItemizingEP10gfxTextRunPKcjj+0x1de)[0xb7966722]
/usr/lib/xulrunner-1.9.0.3/libxul.so(_ZN17gfxPangoFontGroup11InitTextRunEP10gfxTextRunPKcjji+0x33)[0xb7966975]
/usr/lib/xulrunner-1.9.0.3/libxul.so(_ZN17gfxPangoFontGroup11MakeTextRunEPKhjPKN17gfxTextRunFactory10ParametersEj+0x1a8)[0xb7966cb8]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb796209e]
/usr/lib/xulrunner-1.9.0.3/libxul.so(_ZN19gfxTextRunWordCache11MakeTextRunEPKhjP12gfxFontGroupPKN17gfxTextRunFactory10ParametersEj+0x35)[0xb7962143]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73426af]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7342813]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7342c15]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7342ad3]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73430eb]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7343406]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7345488]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7345745]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb72fc74e]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7305ad7]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7305eca]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c924a]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c8294]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7316016]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c924a]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c8294]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c924a]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c8294]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c924a]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c8294]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c924a]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c8294]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7316016]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c924a]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c8294]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c924a]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c8294]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73e216c]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c69b8]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73cad3c]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c715d]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c69b8]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73cb86a]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c715d]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c69b8]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb73c843f]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7302ff6]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7349ac4]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb72e5477]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb72e893c]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb72e8a72]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb72e8b5d]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb752825d]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7522f7c]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7866630]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7861ec8]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7862429]
/usr/lib/libgtk-x11-2.0.so.0[0xb678f036]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb6bcec4b]
/usr/lib/libgobject-2.0.so.0[0xb6be5095]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:01 909377     /usr/lib/firefox-3.0.3/firefox
0804f000-08050000 r--p 00006000 08:01 909377     /usr/lib/firefox-3.0.3/firefox
08050000-08051000 rw-p 00007000 08:01 909377     /usr/lib/firefox-3.0.3/firefox
08a0a000-0bd7e000 rw-p 08a0a000 00:00 0          [heap]
a81fc000-a81fd000 ---p a81fc000 00:00 0 
a81fd000-a89fd000 rwxp a81fd000 00:00 0 
a89fd000-a89fe000 ---p a89fd000 00:00 0 
a89fe000-a91fe000 rwxp a89fe000 00:00 0 
aa200000-aa355000 ---p aa200000 00:00 0 
aa355000-aa356000 rw-p aa355000 00:00 0 
aa356000-aa48f000 ---p aa356000 00:00 0 
aa48f000-aa490000 rw-p aa48f000 00:00 0 
aa490000-aa503000 ---p aa490000 00:00 0 
aa503000-aa509000 rw-p aa503000 00:00 0 
aa509000-aa5c0000 ---p aa509000 00:00 0 
aa5c0000-ab200000 rw-p aa5c0000 00:00 0 
ab200000-ab2fd000 rw-p ab200000 00:00 0 
ab2fd000-ab300000 ---p ab2fd000 00:00 0 
ab300000-ab3ec000 rw-p ab300000 00:00 0 
ab3ec000-ab400000 ---p ab3ec000 00:00 0 
ab400000-ab4ff000 rw-p ab400000 00:00 0 
ab4ff000-ab500000 ---p ab4ff000 00:00 0 
ab5a6000-ab700000 r--p 00000000 08:01 1279545    /usr/share/fonts/truetype/ttf-sil-charis/CharisSILBI.ttf
ab700000-ab7fd000 rw-p ab700000 00:00 0 
ab7fd000-ab800000 ---p ab7fd000 00:00 0 
ab800000-ab8c9000 rw-p ab800000 00:00 0 
ab8c9000-ab900000 ---p ab8c9000 00:00 0 
ab900000-ab9c1000 rw-p ab900000 00:00 0 
ab9c1000-aba00000 ---p ab9c1000 00:00 0 
abda3000-adda4000 rw-p abda3000 00:00 0 
addda000-adf3a000 r--p 00000000 08:01 1279546    /usr/share/fonts/truetype/ttf-sil-charis/CharisSILI.ttf
adfb7000-ae001000 rw-s 00000000 00:09 2228242    /SYSV00000000 (deleted)
ae035000-ae093000 rw-s 00000000 00:09 2261011    /SYSV00000000 (deleted)
ae1c6000-ae1c7000 ---p ae1c6000 00:00 0 
ae1c7000-ae9c7000 rwxp ae1c7000 00:00 0 
ae9c7000-ae9c9000 r-xp 00000000 08:01 13459527   /lib/libkeyutils-1.2.so
ae9c9000-ae9cb000 rw-p 00001000 08:01 13459527   /lib/libkeyutils-1.2.so
ae9cb000-ae9d2000 r-xp 00000000 08:01 837709     /usr/lib/libkrb5support.so.0.1
ae9d2000-ae9d3000 r--p 00006000 08:01 837709     /usr/lib/libkrb5support.so.0.1
ae9d3000-ae9d4000 rw-p 00007000 08:01 837709     /usr/lib/libkrb5support.so.0.1
ae9d4000-ae9ea000 r-xp 00000000 08:01 836976     /usr/lib/libsasl2.so.2.0.22
ae9ea000-ae9eb000 r--p 00015000 08:01 836976     /usr/lib/libsasl2.so.2.0.22
ae9eb000-ae9ec000 rw-p 00016000 08:01 836976     /usr/lib/libsasl2.so.2.0.22
ae9ec000-ae9f8000 r-xp 00000000 08:01 836068     /usr/lib/liblber-2.4.so.2.1.0
ae9f8000-ae9f9000 r--p 0000b000 08:01 836068     /usr/lib/liblber-2.4.so.2.1.0
ae9f9000-ae9fa000 rw-p 0000c000 08:01 836068     /usr/lib/liblber-2.4.so.2.1.0
ae9fa000-aeb2c000 r-xp 00000000 08:01 868536     /usr/lib/i686/cmov/libcrypto.so.0.9.8
aeb2c000-aeb34000 r--p 00132000 08:01 868536     /usr/lib/i686/cmov/libcrypto.so.0.9.8
aeb34000-aeb41000 rw-p 0013a000 08:01 868536     /usr/lib/i686/cmov/libcrypto.so.0.9.8
aeb41000-aeb45000 rw-p aeb41000 00:00 0 
aeb45000-aeb87000 r-xp 00000000 08:01 868537     /usr/lib/i686/cmov/libssl.so.0.9.8
aeb87000-aeb88000 r--p 00041000 08:01 868537     /usr/lib/i686/cmov/libssl.so.0.9.8
aeb88000-aeb8b000 rw-p 00042000 08:01 868537     /usr/lib/i686/cmov/libssl.so.0.9.8
aeb8b000-aebb3000 r-xp 00000000 08:01 837564     /usr/lib/libgssapi_krb5.so.2.2
aebb3000-aebb4000 r--p 00028000 08:01 837564     /usr/lib/libgssapi_krb5.so.2.2
aebb4000-aebb5000 rw-p 00029000 08:01 837564     /usr/lib/libgssapi_krb5.so.2.2
aebb5000-aebd7000 r-xp 00000000 08:01 837701     /usr/lib/libk5crypto.so.3.1
aebd7000-aebd8000 r--p 00022000 08:01 837701     /usr/lib/libk5crypto.so.3.1
aebd8000-aebd9000 rw-p 00023000 08:01 837701     /usr/lib/libk5crypto.so.3.1
aebd9000-aec68000 r-xp 00000000 08:01 837707     /usr/lib/libkrb5.so.3.3
aec68000-aec6a000 r--p 0008e000 08:01 837707     /usr/lib/libkrb5.so.3.3
aec6a000-aec6b000 rw-p 00090000 08:01 837707     /usr/lib/libkrb5.so.3.3
aec6b000-aecaa000 r-xp 00000000 08:01 836070     /usr/lib/libldap_r-2.4.so.2.1.0
aecaa000-aecab000 r--p 0003e000 08:01 836070     /usr/lib/libldap_r-2.4.so.2.1.0
aecab000-aecac000 rw-p 0003f000 08:01 836070     /usr/lib/libldap_r-2.4.so.2.1.0
aecac000-aecad000 rw-p aecac000 00:00 0 
aecad000-aecdd000 r-xp 00000000 08:01 837683     /usr/lib/libidn.so.11.5.37
aecdd000-aecde000 r--p 00030000 08:01 837683     /usr/lib/libidn.so.11.5.37
aecde000-aecdf000 rw-p 00031000 08:01 837683     /usr/lib/libidn.so.11.5.37
aecdf000-aed1b000 r-xp 00000000 08:01 836017     /usr/lib/libcurl.so.4.1.0
aed1b000-aed1c000 r--p 0003c000 08:01 836017     /usr/lib/libcurl.so.4.1.0
aed1c000-aed1d000 rw-p 0003d000 08:01 836017     /usr/lib/libcurl.so.4.1.0
aed2e000-aed2f000 ---p aed2e000 00:00 0 
aed2f000-af52f000 rwxp aed2f000 00:00 0 
af52f000-af530000 ---p af52f000 00:00 0 
af530000-afd30000 rwxp af530000 00:00 0 
afd30000-b010a000 rw-p afd30000 00:00 0 
b010a000-b0130000 ---p b010a000 00:00 0 
b0130000-b0251000 rw-p b0130000 00:00 0 
b0251000-b02a8000 ---p b0251000 00:00 0 
b02a8000-b02a9000 rw-p b02a8000 00:00 0 
b02a9000-b02c4000 ---p b02a9000 00:00 0 
b02c4000-b02ca000 rw-p b02c4000 00:00 0 
b02ca000-b0

```

[http://pastebin.com/m5518268a](http://pastebin.com/m5518268a)

UPDATE: 
As I was typing this message, Firefox crashed with this error:
```

firefox: /build/buildd/cairo-1.8.0/src/cairo-ft-font.c:622: _cairo_ft_unscaled_font_unlock_face: Assertion `unscaled->lock_count > 0' failed.
Aborted (core dumped)

```

---

### Post by jfernyhough on 2008-10-20
Does your xorg.conf have entries for fonts?

Make a backup (though one will be made automatically) then try

$ sudo dpkg-reconfigure -phigh xserver-org

This will return it to default, and hopefully will make X find the fonts.

If this does nothing to help, run synaptic, do a search for TTF and check the ubuntu ones are installed - I'm wondering if one has gone missing.

Finally, it could be down to a locale setting. Check under Administration, Language Support and see what your default language is - you may be prompted that packages are missing.

---

### Post by Sslaxx on 2008-10-20
This looks like it might be a Cairo/Pango problem. I'm currently experiencing the same issues. It's making the Save/Cancel buttons on editing a post a non-uniform size, for example.

---

