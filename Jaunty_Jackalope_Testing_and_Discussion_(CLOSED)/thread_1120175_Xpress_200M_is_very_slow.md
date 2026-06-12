---
title: "Xpress 200M is very slow"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sergks on 2009-04-08
glxgears in Jaunty:
1454 frames in 5.0 seconds = 290.765 FPS
1737 frames in 5.0 seconds = 347.231 FPS
1365 frames in 5.1 seconds = 269.623 FPS
1718 frames in 5.0 seconds = 343.483 FPS

I had above 1100 FPS in 8.10. The full details about this bug can be found here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569")
Can this be fixed before the release?  Very disappointed.

---

### Post by sergks on 2009-04-09
Does somebody have the same problem with older ATI cards or only me?

---

### Post by pferraro on 2009-04-09
If you revert your AccelMethod back to XAA, are you able to get the same perf numbers?

---

### Post by sergks on 2009-04-09
No.Unfortunately, XAA does not work for me. In 8.10, I tried the same driver - 6.12.1 and the same libdrm. They gave me above 1200 FPS in glxgears. In the standard 8.10 I had 1000-1100. Now, only 350. :confused:

---

### Post by sergks on 2009-04-20
Update: 
I tried PlanetPenguin Racer instead of glxgears, as psyke83 suggested [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1130582"), and got only 8-10 FPS. So, something is definitely broken for Xpress 200m. This is the first time I notice a significant performance regression for this card under Ubuntu. :(

---

### Post by pferraro on 2009-04-20
In intrepid, this card was supported by the closed source fglrx driver.  The fglrx version in jaunty no longer supports this card - forcing you to use the open source ati driver.  This would certainly account for the loss of opengl performance.
Are you certain you were using the open source ati driver in intrepid?
One of my machines also has this card.  I had to override several X options to get satisfactory opengl and xrender acceleration.  I can provide these if interested.

---

### Post by paradigm2 on 2009-04-20
> **pferraro said:**
> In intrepid, this card was supported by the closed source fglrx driver.  The fglrx version in jaunty no longer supports this card - forcing you to use the open source ati driver.  This would certainly account for the loss of opengl performance.
Are you certain you were using the open source ati driver in intrepid?
One of my machines also has this card.  I had to override several X options to get satisfactory opengl and xrender acceleration.  I can provide these if interested.

Yes, please do provide.

---

### Post by sergks on 2009-04-20
> **pferraro said:**
> Are you certain you were using the open source ati driver in intrepid?
Absolutely. I used the latest driver from git in Intrepid. I believe the latest was 6.12.1. Since OS driver worked well for me, I even did not try to install fglrx. I also used updated libdrm. The newest libdrm + 6.12.1 gave me around 1200 FPS in glxgears and I expected the same in Jaunty.
Now, I do not know what to do - the downgrading will take a lot of time.   
 
> One of my machines also has this card. I had to override several X options to get satisfactory opengl and xrender acceleration. I can provide these if interested. 
I would like to try your options. Thank you in advance.

---

### Post by sergks on 2009-04-20
I have just tried Fedora 11 LiveCD - the same regression. Glxgears  gave only 130 - 150 FPS.

---

### Post by Pro75357 on 2009-04-21
Hello,

I have the same card and the same problem.  I used fglrx in 8.10 because it enabled the capability to suspend to ram.  I tried installing fglrx in 9.04 and X wouldn't start. So, I'm stuck with shutting down all the time.  HOWEVER, compiz seems to work much nicer with this open source driver.  With fglrx, firefox would scroll painfully slow and use 100% cpu if compiz was enabled- this being fixed is a step in the right direction for me.  Now, if they could only get s2r to work...

---

### Post by scradock on 2009-04-21
> **Pro75357 said:**
> Hello,

I have the same card and the same problem.  I used fglrx in 8.10 because it enabled the capability to suspend to ram.  I tried installing fglrx in 9.04 and X wouldn't start. So, I'm stuck with shutting down all the time.  HOWEVER, compiz seems to work much nicer with this open source driver.  With fglrx, firefox would scroll painfully slow and use 100% cpu if compiz was enabled- this being fixed is a step in the right direction for me.  Now, if they could only get s2r to work...

I have an ATI Radeon Xpress 200M, and am experiencing similar slowness in jaunty.

I have, however, dealt with a screen re-draw failure with compositing window managers and Wine (by forcing XAA acceleration in xorg.conf) 

AND got suspend to ram (and waking up again!) to work by removing ALL video quirks. They are now specified in a HAL fdi file, but my machine was not included in the file provided. I added a suitable matching protocol and set power_management.quirk.none to true. The file is 20-video-quirk-pm-hp.fdi in /usr/share/hal/fdi/information/10freedesktop/

HTH

---

### Post by Reiger on 2009-04-21
I have the Xpress 200M card using the radeon open source driver in my laptop. Output of "sudo lshw -C display" is as follows:
```

  *-display UNCLAIMED
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=64 mingnt=8

```

I have Kubuntu Jaunty (as well as the Gnome environment off the same installation), and I can run a whole bunch of desktop effects just fine. Yes, glxgears shows
```

1610 frames in 5.0 seconds = 321.850 FPS
1686 frames in 5.0 seconds = 337.112 FPS
1768 frames in 5.0 seconds = 353.551 FPS

```

I have an ASUS X51RL laptop with 2GB of "DIMM DDR Synchronous" (from lshw) and a "Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz" (also verbatim from lshw). (Originally 1GB of RAM, but I added one way back on Intrepid along with a better wifi card.)

---

### Post by sergks on 2009-04-21
There is a solution to this problem. Alex Deucher provided me with this link:[http://www.nabble.com/R300-regression-td23108996.html]("http://www.nabble.com/R300-regression-td23108996.html") 
I patched r300_context.c, re-compiled the mesa and now I am back:
glxgears
5655 frames in 5.0 seconds = 1130.871 FPS
5656 frames in 5.0 seconds = 1131.106 FPS
5654 frames in 5.0 seconds = 1130.648 FPS

**The solution is preliminary, though. It may result in lockups on some systems.**
Have not seen any so far with my 200m.

---

### Post by hgergo on 2009-04-21
Same problem here the 200M video card is weary slow whi 9.04.
And some bad news ati is not making drier fol old video cards for ubuntu 9.04 :(
And when i will extend the desctop too on an external monitor on both the displays i can see nothing

---

### Post by paradigm2 on 2009-04-21
> **sergks said:**
> There is a solution to this problem. Alex Deucher provided me with this link:[http://www.nabble.com/R300-regression-td23108996.html]("http://www.nabble.com/R300-regression-td23108996.html") 
I patched r300_context.c, re-compiled the mesa and now I am back:
glxgears
5655 frames in 5.0 seconds = 1130.871 FPS
5656 frames in 5.0 seconds = 1131.106 FPS
5654 frames in 5.0 seconds = 1130.648 FPS

**The solution is preliminary, though. It may result in lockups on some systems.**
Have not seen any so far with my 200m.

Thanks.  Can you give us some info on the instructions you used to compile mesa?  What sources did you grab, etc?

It looks pretty complicated.

---

### Post by sergks on 2009-04-21
I did this in a very stupid way (i am not a developer):
1) download mesa_7_4.tar.gz from here: [http://cgit.freedesktop.org/mesa/mesa/]("http://cgit.freedesktop.org/mesa/mesa/");
2) unpack the archive;
3) modify r300_context.c file (/src/mesa/drivers/dri/r300/r300_context.c) - you have to move 'ctx->VertexProgram._MaintainTnlProgram = GL_TRUE;' to another location (see the patch);
4) sudo apt-get build-dep mesa;
5) ./autogen.sh (if you do not have autoconf: sudo apt-get install autoconf);
autoconf will show you any other dependencies you need - install them;
6) make;
7) backup r300_dri.so in /usr/lib/dri (r300_dri.so -> r300_dri.so.bak), you can do this with sudo nautilus;
8.) move r300_dri.so from your build (should be in /lib) to /usr/lib/dri;
9) restart your system;
10) check glxgears.

The idea is to re-place r300_dri.so with modified one. I know this is not the best way but worked for me.

---

### Post by sergks on 2009-04-21
The patch command did not work for me. So, I modified r300_context.c file manually.

---

### Post by paradigm2 on 2009-04-21
> **sergks said:**
> I did this in a very stupid way (i am not a developer):
1) download mesa_7_4.tar.gz from here: [http://cgit.freedesktop.org/mesa/mesa/]("http://cgit.freedesktop.org/mesa/mesa/");
2) unpack the archive;
3) modify r300_context.c file (/src/mesa/drivers/dri/r300/r300_context.c) - you have to move 'ctx->VertexProgram._MaintainTnlProgram = GL_TRUE;' to another location (see the patch);
4) sudo apt-get build-dep mesa;
5) ./autogen.sh (if you do not have autoconf: sudo apt-get install autoconf);
autoconf will show you any other dependencies you need - install them;
6) make;
7) backup r300_dri.so in /usr/lib/dri (r300_dri.so -> r300_dri.so.bak), you can do this with sudo nautilus;
8.) move r300_dri.so from your build (should be in /lib) to /usr/lib/dri;
9) restart your system;
10) check glxgears.

The idea is to re-place r300_dri.so with modified one. I know this is not the best way but worked for me.

Thanks, I appreciate it.  I will give it a go tonight and report back.  I'm thinking this still should work even though I upgraded my kernel to 2.6.30rc2 because I also installed the proper headers and kernel source.

edit: Just to confirm and looking at the patch provided in the link:

```

diff --git a/src/mesa/drivers/dri/r300/r300_context.c b/src/mesa/drivers/dri/r300/r300_context.c
index 12bee1a..4de95f1 100644
--- a/src/mesa/drivers/dri/r300/r300_context.c
+++ b/src/mesa/drivers/dri/r300/r300_context.c
@@ -374,7 +374,6 @@ GLboolean r300CreateContext(const __GLcontextModes * glVisual,
  ctx->Const.FragmentProgram.MaxNativeTexIndirections =
     PFS_MAX_TEX_INDIRECT;
  ctx->Const.FragmentProgram.MaxNativeAddressRegs = 0; /* and these are?? */
- ctx->VertexProgram._MaintainTnlProgram = GL_TRUE;
  ctx->FragmentProgram._MaintainTexEnvProgram = GL_TRUE;
 
  driInitExtensions(ctx, card_extensions, GL_TRUE);
@@ -421,7 +420,8 @@ GLboolean r300CreateContext(const __GLcontextModes * glVisual,
  }
  TCL_FALLBACK(r300->radeon.glCtx,
      RADEON_TCL_FALLBACK_TCL_DISABLE, 1);
- }
+ } else
+ ctx->VertexProgram._MaintainTnlProgram = GL_TRUE;
 
  return GL_TRUE;
 } 

```

It appears that there is actually more than just the one line changed.

You did all of the above changes manually, right?

---

### Post by sergks on 2009-04-21
> **paradigm2 said:**
> It appears that there is actually more than just the one line changed. You did all of the above changes manually, right?

You are right. I did all changes as suggested in the patch. Minus means remove the line, plus means add the line. The locations were different, though, and I do not know why (most probably, they wrote this patch for the git version). So, you have to find the locations.
After that:  
1) remove this line: ctx->VertexProgram._MaintainTnlProgram = GL_TRUE;
2) remove this line: }
3) add these two lines:
      } else
        ctx->VertexProgram._MaintainTnlProgram = GL_TRUE;

Four changes only.
Good luck.

---

### Post by pferraro on 2009-04-21
> **sergks said:**
> I would like to try your options. Thank you in advance.

From 'man radeon':
Option "EnablePageFlip" "on"
Option "AccelDFS" "on"
Option "FBTexPercent" "0"

From 'man exa':
Option "EXAOptimizeMigration" "true"
Option "MigrationHeuristic" "smart"
(experiment with "greedy" as well)

Server options:
Option "BackingStore" "true"

---

### Post by sergks on 2009-04-21
Thanks, pferraro. I will try them

---

### Post by paradigm2 on 2009-04-21
> **sergks said:**
> You are right. I did all changes as suggested in the patch. Minus means remove the line, plus means add the line. The locations were different, though, and I do not know why (most probably, they wrote this patch for the git version). So, you have to find the locations.
After that:  
1) remove this line: ctx->VertexProgram._MaintainTnlProgram = GL_TRUE;
2) remove this line: }
3) add these two lines:
      } else
        ctx->VertexProgram._MaintainTnlProgram = GL_TRUE;

Four changes only.
Good luck.

SUCCESS!  

```

2566 frames in 5.0 seconds = 513.188 FPS
2562 frames in 5.0 seconds = 512.359 FPS
2568 frames in 5.0 seconds = 513.499 FPS
2556 frames in 5.0 seconds = 511.035 FPS
3502 frames in 5.0 seconds = 700.379 FPS
4497 frames in 5.0 seconds = 899.288 FPS

```

Performance is at least doubled.  Thank you very much!  Your instructions were very good. :)

My next question is how do I lock this so that synaptic or the update-manager does not install a "new" r300 driver wiping out this one?

---

### Post by tricolorpoa on 2009-04-22
Sorry for my English.. 

I compiled mesa_7_4 but don't have any file called r300_dri.so on /lib

Need some extra package before compile ?

thanks!

---

### Post by psyke83 on 2009-04-22
I haven't followed this process as I don't own any ATI hardware, but... come on, guys. There's no need to compile from vanilla source, use the deb sources!

```
$ apt-get source mesa
```

When you edit the source, you can build your own packages using something like:
```
$ sudo dpkg-buildpackage
```

The advantage is a much cleaner system - since you're installing deb packages, you can easily roll-back or upgrade packages in the future, and you won't have to track potentially hundreds of misplaced files placed in the wrong path (which can happen if you don't set the --prefix flags properly in the vanilla source's configure scripts).

---

### Post by tricolorpoa on 2009-04-22
> **tricolorpoa said:**
> Sorry for my English.. 

I compiled mesa_7_4 but don't have any file called r300_dri.so on /lib

Need some extra package before compile ?

thanks!

It's my fault!

just run 

make realclean
./autogen.sh

Installed all dependencies and run

make

And the r300_dri.so come to /lib

but,
glxgears 
259 frames in 5.0 seconds = 51.764 FPS
275 frames in 5.0 seconds = 54.836 FPS
277 frames in 5.0 seconds = 55.244 FPS
279 frames in 5.0 seconds = 55.673 FPS
251 frames in 5.0 seconds = 50.173 FPS

:confused:

---

### Post by Pro75357 on 2009-04-22
> **scradock said:**
> I have an ATI Radeon Xpress 200M, and am experiencing similar slowness in jaunty.

I have, however, dealt with a screen re-draw failure with compositing window managers and Wine (by forcing XAA acceleration in xorg.conf) 

AND got suspend to ram (and waking up again!) to work by removing ALL video quirks. They are now specified in a HAL fdi file, but my machine was not included in the file provided. I added a suitable matching protocol and set power_management.quirk.none to true. The file is 20-video-quirk-pm-hp.fdi in /usr/share/hal/fdi/information/10freedesktop/

HTH

Thanks for your reply, but after trying your suggestion this laptop still will not awake from standby,  even though lshal reports: power_management.quirk.none = true. If you have anymore suggestions, I'm willing to try anything at this point.  

Pro

---

### Post by danwood76 on 2009-04-22
By the way you cannot lock this package unless you build the ubuntu (debian) way.
As mentioned by psyke83.

```

1) cd to your source directory (or where you want to build)
2) apt-get source mesa
3) sudo apt-get build-dep mesa
4) patch the file
5) cd mesa-7.4
6) dpkg-buildpackage
7) install debs

```
then you can lock the version in synaptic and will have all the ubuntu patches.

---

### Post by sergks on 2009-04-22
> **psyke83 said:**
> I haven't followed this process as I don't own any ATI hardware, but... come on, guys. There's no need to compile from vanilla source, use the deb sources!

Thanks, psyke83. Since I hurry to check the patch I even did not think about the Ubuntu way. I have very limited experience with compiling from sources.

---

### Post by sergks on 2009-04-22
> **tricolorpoa said:**
> 
glxgears 
259 frames in 5.0 seconds = 51.764 FPS
275 frames in 5.0 seconds = 54.836 FPS
277 frames in 5.0 seconds = 55.244 FPS
279 frames in 5.0 seconds = 55.673 FPS
251 frames in 5.0 seconds = 50.173 FPS

:confused:

What ATI card do you have? This patch may work only for R300 cards.

---

### Post by tricolorpoa on 2009-04-22
```
root@turion:~# lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

```I think my VGA Card is diferent..

```
root@turion:~# lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=66 mingnt=8

```Everything works fine before the update to jaunty..
Now I'm not able to active special effects..

```
root@turion:~# cat /etc/X11/xorg.conf
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "ati"
EndSection

```what's wrong with my VGA Card?:(

---

### Post by danwood76 on 2009-04-22
Remove the 
```

Section "Module"
    Load    "glx"
EndSection

```
Section and also remove 'Driver "ati"' as it is not needed.
Then reload X and see if its better.

---

### Post by tricolorpoa on 2009-04-22
> **danwood76 said:**
> Remove the 
```

Section "Module"
    Load    "glx"
EndSection

```Section and also remove 'Driver "ati"' as it is not needed.
Then reload X and see if its better.

even after the alterations the problem continues..
When I try to enable special effects a message say that there's no driver avaliable and then my Gnome continues without any effect...

:(

---

### Post by sergks on 2009-04-23
tricolorpoa, I have exactly the same card as you and this card should work fine with Compiz in Jaunty. You can try LiveCD and run glxgears there.
By the way, did you install fglrx in Intrepid? This may explain the loss in performance in Jaunty.

---

### Post by tricolorpoa on 2009-04-23
Thanks for your atention sergks..
I never installed fglrx before, but in Intrepid the performance of my VGA Card was good.
After the upgrade not.
I looking for "Restricted Drivers Manager" but it isn't pop-up...
In System > Administration there are only "Hardware Driver" but Athero is the only one to be actived...

How can I know if I am using restricted driver for my ati VGA card?
What can I do to save my Ubuntu?

---

