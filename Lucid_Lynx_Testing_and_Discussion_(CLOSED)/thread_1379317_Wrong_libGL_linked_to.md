---
title: "Wrong libGL linked to"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by NightMKoder on 2010-01-12
Seems like the latest updates linked to libGL.so.1 => /usr/lib/mesa/libGL.so.1 rather than /usr/lib/libGL.so.1 , possibly because the latter doesn't exist.

This is very problematic for proprietary drivers, and also seems just plain wrong. glxgears, glxinfo and kwin are some of the casualties.

---

### Post by SevenMachines on 2010-01-12
the new nvidia drivers should now be using the alternatives system. as far as i'm aware there shouldnt be a /usr/lib/libGL* and that these libraries are now in /usr/lib/mesa and /usr/lib/nvidia-current/ and so on. the correct ones should be being used by /etc/alternatives/ for example, for nvidia-current i have
/etc/alternatives/gl_conf -> /usr/lib/nvidia-current/ld.so.conf
and
/etc/alternatives/gl_libraries -> /usr/lib/nvidia-current

{EDIT] just to add, i dont know how the other proprietary drivers are doing this at the moment

---

### Post by afv on 2010-01-12
[Bug #506547 (Some GL apps won't run: libGLU.so.1: No such file or directory)](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/506547).

---

### Post by NightMKoder on 2010-01-12
> **SevenMachines said:**
> the new nvidia drivers should now be using the alternatives system. as far as i'm aware there shouldnt be a /usr/lib/libGL* and that these libraries are now in /usr/lib/mesa and /usr/lib/nvidia-current/ and so on. the correct ones should be being used by /etc/alternatives/ for example, for nvidia-current i have
/etc/alternatives/gl_conf -> /usr/lib/nvidia-current/ld.so.conf
and
/etc/alternatives/gl_libraries -> /usr/lib/nvidia-current

{EDIT] just to add, i dont know how the other proprietary drivers are doing this at the moment

That may be true, but neither kwin nor glx* should depend on explicit mesa libGL, which is what they do now. They should either be using the alternatives path or the libGL outside of the mesa directory in /usr/lib.

---

### Post by SevenMachines on 2010-01-12
i'm not having any problems with either glxinfo or glxgears and i have no /usr/lib/libGL* so i'm not sure whats going on

[EDIT] they're both finding and using the nvidia libraries in /usr/lib/nvidia-current which is my set alternative at the moment

---

### Post by mc4man on 2010-01-13
> i have no /usr/lib/libGL* so ..

Links for libGL.so and libGLU.so, plus a link for libGLU.a are added to /usr/lib when installing the  current libgl1-mesa-dev and libglu1-mesa-dev packages

The main reason is while the .pc's were correct (previous update), many sources being built off of those libraries could find the headers but were unable to link to the *.so's

Now everything works well in that regard.

---

### Post by SevenMachines on 2010-01-13
thanks mc4man, good to know. 
will having a 'default' mesa libGL in /usr/lib/libGL.so -> mesa/libGL.so from libgl1-mesa-dev while actually using the alternatives version from nvidia-current not cause problems though? 
still can't get any of the issues [NightMKoder]("http://ubuntuforums.org/member.php?u=702614") was having but knowing nothing about dpkg alternatives i'm a little confused

---

### Post by mc4man on 2010-01-13
> will having a 'default' mesa libGL in /usr/lib/libGL.so -> mesa/libGL.so from libgl1-mesa-dev while actually using the alternatives version from nvidia-current not cause problems though

I don't think so, though I also not sure everything is set quite yet.

As an example, when the first update moved the libGl's to /usr/lib I was unable to build vlc, failed on -lGL
Creating a link in /usr/lib allowed the build to succeed, and after the build, to test, I deleted the link in /usr/lib which had no affect on the vlc install.

They're there only to assist building, (at least from what I can see.

see [here ]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/505359")for some ldd's and bug 

While over the weekend I could build mplayer w/ vdpau, I had to hack around the fact that that nvidia-current-dev removed libgl1-mesa-dev, that's been fixed, but haven't tried again since.

(to some extent a lot of this is a bit premature anyway

I'd like to also sometime see if from an A2++ install  one could go to your ppa (195) and maintain glx, compiz and building ect.

---

### Post by SevenMachines on 2010-01-13
i fiddled around with things a little with different combinations of packages and a little test program and it doesn't seem to cause any problems so hopefully all is fine. it only seems to get used, at least as far as i can find, when linking as you say.
i was leaving any updates on my beta playing ppa since there was going to be some packaging changes, always easier to use the ones in the repository and just update them for messing around with betas

---

### Post by mc4man on 2010-01-14
There was one more update that basically moved the libGLU libs back into /usr/lib where from my perspective they belonged -(building off of

Though it also appears when in /usr/lib/mesa they also affected other things.

Other than jockey not working quite right the 190. drivers should set up fairly easy (manually install nvidia-current and the settings packages, run sudo nvidia-xconfig and restart

---

### Post by afv on 2010-01-14
This is solved.

> 
mesa (7.7-0ubuntu5) lucid; urgency=low

 * debian/rules:
   - Remove invalid "install -d" command.
   - Do not pass --libdir=/usr/lib/mesa flag any more.
 * debian/libgl1-mesa-dev.install, libgl1-mesa-swx11-dev.install,
   libgl1-mesa-swx11.install, libglu1-mesa-dev.install,
   libglu1-mesa.install:
   - Install *.pc files in /usr/lib/pkgconfig instead of
     /usr/lib/mesa/pkgconfig.
   - Do not Install libGLU* in /usr/lib/mesa (LP: #506547).
 * debian/libglu1-mesa-dev.links:
   - Remove file as we install libGLU in the right place now.

Date: Wed, 13 Jan 2010 20:18:17 +0100
Changed-By: Alberto Milone <alberto.milone@canonical.com>
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
[https://launchpad.net/ubuntu/lucid/+source/mesa/7.7-0ubuntu5](https://launchpad.net/ubuntu/lucid/+source/mesa/7.7-0ubuntu5)


---

### Post by tghe-retford on 2010-01-15
KWin is still broken for me, regardless of whether you use Sevenmachines PPA or the official NVidia drivers in the Lucid repositories. OpenGL rendering just doesn't want to play, whilst XRender does (but with some effects disabled). Last update just about an hour ago, if less.

---

