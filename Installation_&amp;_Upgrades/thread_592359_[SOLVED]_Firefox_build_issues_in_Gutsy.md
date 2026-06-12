---
title: "[SOLVED] Firefox build issues in Gutsy"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by glennric on 2007-10-26
I am trying to compile Firefox 2.0.0.8 from source and am having some issues.

The first issue I had was a compilation error while it was building the canvas stuff for Firefox.  Then I found this
[http://live.gnome.org/JhbuildIssues/mozilla#head-65db9063bcddde7c04521924fcdecd6393972a5f]("http://live.gnome.org/JhbuildIssues/mozilla#head-65db9063bcddde7c04521924fcdecd6393972a5f")
which resolved that issue and Firefox compiled.

I installed the resulting build into the opt directory and tried to run /opt/firefox/firefox from a terminal.  All that happened was I got a message saying, "Cannot find mozilla runtime directory. Exiting."  Inspecting the files in the /opt/firefox directory I noticed that run-mozilla.sh did not have read and execute permissions for everyone.  So I added those.  Now I don't get the above message, but nothing happens.  Firefox doesn't start.  "ps aux" doesn't show any firefox processes running.  It just exits the startup scripts.

I was able to compile Firefox 2.0.0.7 while I was still running Feisty and that build still runs fine in Gutsy.  I want to have a build of Firefox that is optimized for my processor.  Has anyone else had this issue?  Does anyone know how to solve it?

I have attached my .mozconfig file if this helps.

---

### Post by glennric on 2007-10-26
I noticed that the gutsy version of firefox is compiled with gcc-4.2, but that the default version of gcc for gutsy is gcc-4.1.  Does this have anything to do with the problem?

---

### Post by FredB on 2007-10-26
Your .mozconfig is too big and nearly completely useless.

Start with a .mozconfig like the one "officially" used by mozilla itself.

Tinderboxes for gecko 1.8.x.y  (fx 2.0.0.x) are here :

[http://tinderbox.mozilla.org/showbuilds.cgi?tree=Mozilla1.8](http://tinderbox.mozilla.org/showbuilds.cgi?tree=Mozilla1.8)

```
#. $topsrcdir/browser/config/mozconfig

export MOZILLA_OFFICIAL=1

mk_add_options MOZ_CO_PROJECT="browser"
#. $topsrcdir/browser/config/mozconfig

export MOZILLA_OFFICIAL=1

mk_add_options MOZ_CO_PROJECT="browser"
mk_add_options MOZ_MAKE_FLAGS="-j2"

ac_add_options --enable-application="browser"
ac_add_options --disable-debug
ac_add_options --enable-optimize="-Os -freorder-blocks -fno-reorder-functions -gstabs+"
ac_add_options --disable-tests
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-xft
ac_add_options --disable-freetype2
ac_add_options --enable-svg
ac_add_options --enable-canvas

ac_add_options --enable-static
ac_add_options --disable-shared

```

Of course, you can use your own optimization line, but to be sure you had all the depeencies, don't forget to enter :

```
sudo apt-get builddep firefox
```

---

### Post by glennric on 2007-10-26
I don't know how you can say that my mozconfig file is to big and useless.  I have added a little bit to the mozconfig file since I successfully compiled with it when Feisty was installed.  You clearly don't know what you are talking about.  The way I see it, your mozconfig is completely useless.  Why not just run the default Gutsy version if you use that mozconfig.  The point is to optimize the build.

Please read a post carefully before replying with useless information.

---

### Post by FredB on 2007-10-26
> **glennric said:**
> I don't know how you can say that my mozconfig file is to big and useless.

Only 7 years of EXPERIENCE of building mozilla software on my computers... I've built preversion of Mozilla (ancestor of Seamonkey) 0.8...

> I have added a little bit to the mozconfig file since I successfully compiled with it when Feisty was installed.Really ? How many useless options in your .mozconfig ?

> You clearly don't know what you are talking about.Really ? I built preversions of Phoenix 0.1 back in september 2002 ! So, how can I say that ? You missed an occasion to close your mouth. Oooops !

> The way I see it, your mozconfig is completely useless.It is just AN OFFICIAL .mozconfig. Really useless. How can you be so sure of yourself ? Are you better to know what options to use ? Do you know source code better than their coders ?

> Why not just run the default Gutsy version if you use that mozconfigTesting development builds, so you can have firefox 2 !!!!!

Don't you understand that ?

> The point is to optimize the build.So, just modify your optimize line !

> Please read a post carefully before replying with useless information.Useless ? Maybe more useful than your attack on my personnality and my experience.

And for your information, here is my last about :

```
Build identifier: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9a9pre) Gecko/2007102618 Minefield/3.0a9pre
```And my .mozconfig : short BUT USEFUL ! For trunk builds, not 2.0.0.x one. Should have said that before :(

```
#
# See http://www.mozilla.org/build/ for build instructions.
#

export CC=gcc-4.2
export CXX=g++-4.2

. $topsrcdir/browser/config/mozconfig

# Options for 'configure' (same as command-line options).
ac_add_options --enable-optimize="-Os -march=athlon64 -w -pipe"
ac_add_options --disable-debug
ac_add_options --disable-tests

ac_add_options --enable-default-toolkit=cairo-gtk2

ac_add_options --enable-strip
```Abuse reported !

---

### Post by glennric on 2007-10-26
If you read my first post you would see that I have also successfully compiled firefox and with essentially this mozconfig file.  With this mozconfig and every modification I have tried I get the same result that it won't run, as stated in the original post.  The mozconfig I used while still running Feisty, that worked great then, and now won't even compile is attached.  After adding the line 
```
ac_add_options --enable-system-cairo
```
it compiles, but won't run.  I suspect the mozconfig's you posted won't compile either unless you add the above option.  I added the last 15 or so options in an attempt to get the compilation to work.  I did this by emulating the options used to compile the gutsy version, which by the way has a lot more options than your mozconfig and works.  It is not a matter of the size.  You missed the point of my post almost entirely and jumped in with a post assuming that I don't know what I am talking about.

---

### Post by glennric on 2007-10-26
I forgot to post the original mozconfig.  Here it is.

---

### Post by glennric on 2007-10-26
Does anyone have any useful ideas on this issue?  I have tried compiling firefox on several different computers running Gutsy to no avail.  The build will not run.  I know that the mozconfig file I have worked with Feisty, and that it doesn't work with Gutsy.  I even tried compiling Firefox 2.0.0.7 exactly the same way that I did in Feisty and it no longer works in Gutsy.  It is really odd that the file run-mozilla.sh is not given the correct permissions.

---

### Post by FredB on 2007-10-27
> **glennric said:**
> If you read my first post you would see that I have also successfully compiled firefox and with essentially this mozconfig file.  With this mozconfig and every modification I have tried I get the same result that it won't run, as stated in the original post.  The mozconfig I used while still running Feisty, that worked great then, and now won't even compile is attached.

Firefox 2.0.0.8 code get a version of cairo in it, if I remember well. If the system cairo version is not compatible with the one of firefox...

[QUOYE]After adding the line 
```
ac_add_options --enable-system-cairo
```it compiles, but won't run. [/quote]

And if you run it from /dist/bin/ directory, what did it say ?

```
 I suspect the mozconfig's you posted won't compile either unless you add the above option
```.

I don't think so. Will try, but I don't think so.

> I added the last 15 or so options in an attempt to get the compilation to work.  I did this by emulating the options used to compile the gutsy version, which by the way has a lot more options than your mozconfig and works.You don't need all of them. Some are activated by others.

> It is not a matter of the size.  You missed the point of my post almost entirely and jumped in with a post assuming that I don't know what I am talking about.I was just copying you :)

---

### Post by FredB on 2007-10-27
Wrong permission ?!

Well, I looked at your .mozconfig.

You can - I think - remove safely :

ac_add_options --enable-crypto -> enabled by default since Mozilla Suite 0.8 or  something like this.

ac_add_options --enable-xinerema ? Do you have 2 screens ?

Don't know if you heard about this page : [http://webtools.mozilla.org/build/config.cgi](http://webtools.mozilla.org/build/config.cgi) ?

I will try this .mozconfig with 2.0.0.8 source and I will tell you in about 1 hour.

```
. $topsrcdir/browser/config/mozconfig

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@

ac_add_options --with-pthreads
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-official-branding
ac_add_options --disable-freetype2
ac_add_options --enable-single-profile
ac_add_options --enable-extensions=default,xforms,schema-validation
ac_add_options --disable-installer
ac_add_options --disable-tests
ac_add_options --enable-optimize="-O3 -march=athlon-xp -freorder-blocks -fno-reorder-functions -msse -mmmx -m3dnow -mfpmath=sse -D_FORTIFY_SOURCE=2"
ac_add_options --disable-shared
ac_add_options --enable-static
ac_add_options --disable-profilesharing
ac_add_options --disable-debug
ac_add_options --enable-xft
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --enable-update-packaging

```Build process is killed here :

```

/home/fred/download/mozilla/content/canvas/src/nsCanvasRenderingContext2D.cpp:198: attention : «PRBool FloatValidate(double, double, double)" defined but not used
make[5]: *** [nsCanvasRenderingContext2D.o] Erreur 1
make[5]: quittant le répertoire « /home/fred/download/mozilla/obj-x86_64-unknown-linux-gnu/content/canvas/src »
make[4]: *** [libs] Erreur 2
make[4]: quittant le répertoire « /home/fred/download/mozilla/obj-x86_64-unknown-linux-gnu/content/canvas »
make[3]: *** [libs] Erreur 2
make[3]: quittant le répertoire « /home/fred/download/mozilla/obj-x86_64-unknown-linux-gnu/content »
make[2]: *** [tier_9] Erreur 2
make[2]: quittant le répertoire « /home/fred/download/mozilla/obj-x86_64-unknown-linux-gnu »
make[1]: *** [default] Erreur 2
make[1]: quittant le répertoire « /home/fred/download/mozilla/obj-x86_64-unknown-linux-gnu »
make: *** [build] Erreur 2
```Will try the simpler .mozconfig now, this one :

```

export MOZILLA_OFFICIAL=1

mk_add_options MOZ_CO_PROJECT="browser"
. $topsrcdir/browser/config/mozconfig

export MOZILLA_OFFICIAL=1

mk_add_options MOZ_CO_PROJECT="browser"
mk_add_options MOZ_MAKE_FLAGS="-j2"

ac_add_options --enable-application="browser"
ac_add_options --disable-debug
ac_add_options --enable-optimize="-Os -freorder-blocks -fno-reorder-functions -gstabs+"
ac_add_options --disable-tests
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-xft
ac_add_options --disable-freetype2
ac_add_options --enable-svg
ac_add_options --enable-canvas

ac_add_options --enable-static
ac_add_options --disable-shared
```Edit : Ok, I missed --enable-system-cairo. I will use the .mozconfig above adding --enable-system-cairo, which is useless with trunk build (Gran Paradiso / Minefield).

And I will use your optimization line, but replacing athlon-xp by athlon64 because I have 64bits Sempron 3100+.

---

### Post by FredB on 2007-10-27
I finally was able to build a Firefox and it starts under gutsy.

I was using this .mozconfig :

```

export MOZILLA_OFFICIAL=1

. $topsrcdir/browser/config/mozconfig

export MOZILLA_OFFICIAL=1

mk_add_options MOZ_CO_PROJECT="browser"
mk_add_options MOZ_MAKE_FLAGS="-j2"

ac_add_options --enable-application="browser"
ac_add_options --disable-debug
ac_add_options --enable-optimize="-O3 -march=athlon64 -pipe -ftracer -fomit-frame-pointer -freorder-blocks -fno-reorder-functions -msse -mmmx -m3dnow -mfpmath=sse -D_FORTIFY_SOURCE=2"
ac_add_options --disable-tests
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-xft
ac_add_options --disable-freetype2
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --enable-system-cairo

ac_add_options --enable-static
ac_add_options --disable-shared

```

Here is the screenshot that is a proof :

[IMG]http://img520.imageshack.us/img520/6213/screenshot5ft1.png[/IMG]

So, if you want official branding you could use this .mozconfig which perfectly works :

```

. $topsrcdir/browser/config/mozconfig

export MOZILLA_OFFICIAL=1

mk_add_options MOZ_CO_PROJECT="browser"
mk_add_options MOZ_MAKE_FLAGS="-j2"
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-linux-athlon-xp

ac_add_options --enable-application="browser"
ac_add_options --disable-debug
ac_add_options --enable-optimize="-O3 -march=athlon-xp -pipe -ftracer -fomit-frame-pointer -freorder-blocks -fno-reorder-functions -msse -mmmx -m3dnow -mfpmath=sse -D_FORTIFY_SOURCE=2"
ac_add_options --disable-tests
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-xft
ac_add_options --disable-freetype2
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --enable-system-cairo

ac_add_options --enable-static
ac_add_options --disable-shared
ac_add_options --enable-official-branding


```

Hope it will work this time.

---

### Post by glennric on 2007-10-27
Thanks FredB.  I will try that mozconfig and see if it works.  I apologize for being snappy at the beginning of the post (bad day yesterday), and I see that you are still being quite helpful.  A credit to your character.  

I did know about the mozconfig configuration page.  Thanks though.

---

### Post by FredB on 2007-10-27
I was snappy too. As you can see in the screenshot, I've used a short but powerful .mozconfig.

Hope it will work...

---

### Post by glennric on 2007-10-27
Finally!  I solved it.  It turns out it had nothing to do with the .mozconfig file or the build.  The issue was all about file permissions.  I noticed that if I ran the build from the obj-dir*/dist/firefox directory it ran fine.  On the other hand if I untarred into the opt directory and tried to run it from there nothing would happen.  I tried "chmod +r -R /opt/firefox" and "chmod +x /opt/firefox/run-mozilla.sh" and it works fine.  I don't know what has changed from Feisty to Gutsy that makes the file permissions work differently, but that is the problem.

---

### Post by FredB on 2007-10-27
Can't tell you. At least, you have your build, and this is the more important here.

Have a good sunday.

---

### Post by glennric on 2007-10-27
Yep.  I agree.  This is minor.  Now to tweak the build.  At least I learned a little more about the build options.  I will remove some of the redundant ones, although that should make little difference.  I also tried compiling firefox with gcc-4.2, but I got a linker error.  I don't remember the exact details, but I will probably try that again later.

---

### Post by glennric on 2007-10-27
I tried compiling firefox with gcc-4.2 again and got this error:
```
mozilla-decoder.cpp:(.text+0x451): undefined reference to `gdk_pango_context_get'
/usr/bin/ld: firefox-bin: hidden symbol `gdk_pango_context_get' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
```

Any ideas how to fix this?

---

### Post by FredB on 2007-10-28
> **glennric said:**
> I tried compiling firefox with gcc-4.2 again and got this error:
```
mozilla-decoder.cpp:(.text+0x451): undefined reference to `gdk_pango_context_get'
/usr/bin/ld: firefox-bin: hidden symbol `gdk_pango_context_get' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
```Any ideas how to fix this?

Can you show your .mozconfig ? How do you set gcc / g++ 4.2 for building firefox ?

Is enable-pango in your .mozconfig ?

Just trying to help ;)

---

### Post by glennric on 2007-10-28
Yes pango is enabled.  I am going to try to compile it again without that and see what happens.

Here is my .mozconfig:

```
. $topsrcdir/browser/config/mozconfig

export CC=gcc-4.2
export CXX=g++-4.2
export MOZILLA_OFFICIAL=1

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-linux-athlon-xp

ac_add_options --with-pthreads
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-official-branding
ac_add_options --disable-freetype2
ac_add_options --enable-single-profile
ac_add_options --enable-extensions=default,xforms,schema-validation
ac_add_options --disable-installer
ac_add_options --disable-tests
ac_add_options --enable-optimize="-O3 -march=athlon-xp -pipe -msse -mmmx -m3dnow -mfpmath=sse -D_FORTIFY_SOURCE=2"
ac_add_options --disable-shared
ac_add_options --enable-static
ac_add_options --disable-profilesharing
ac_add_options --disable-debug
ac_add_options --enable-xft
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --enable-update-packaging
ac_add_options --disable-updater
ac_add_options --enable-system-cairo
ac_add_options --enable-pango
ac_add_options --enable-svg-renderer=cairo
```

---

### Post by FredB on 2007-10-28
Well, it could be also a gcc 4.2 bug with firefox code like the --enable-system-cairo one ;). But let's see what's happening without --enable-pango.

Also those two are "in war" :

ac_add_options --enable-update-packaging
ac_add_options --disable-updater

Do you want to enable updater tool or not ?

If you want, remove disable-updater, if not, disable the other option.

Well, just trying to find some clues ;)

---

### Post by glennric on 2007-10-28
I took out the --enable-update-packaging and --enable-pango options and compiled with gcc-4.2 and g++-4.2 and got the following error:
```
/usr/bin/ld: firefox-bin: hidden symbol `nsFileSpecImpl::Create(nsISupports*, nsID const&, void**)' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make[4]: *** [firefox-bin] Error 1
```

---

### Post by FredB on 2007-10-29
I've tried with Sunbird 0.7 source code (which share core code with firefox) and with gcc 4.2 I've got the same error. Looks like to be a bug related to gcc 4.2 and gecko 1.8.1.xx code.

---

### Post by glennric on 2007-10-29
Hmm.  Well, I will stick with the current build for now then.  By the way, if I disable pango  I have noticed some bad font rendering the resulting firefox build.  Particularly with the font used in code blocks on the Ubuntu forums.  I believe this is the monospace fonts.  The same happens in Thunderbird with this option disabled.

---

