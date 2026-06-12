---
title: "What nvidia may be on lucid..."
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mc4man on 2010-01-05
having a spare partition did a 2nd lucid install from the daily and gave [this ppa]("https://launchpad.net/~albertomilone/+archive/proprietary-video-improvements") a try ( the other uses the sevenmachines ppa.

Sorta thinking it may be where lucid is heading.

While it failed to install the 190.xx thru the normal method of admin. -> hardware drivers cleanly (came close), running  sudo nvidia-xconfig I think did the trick. (unfortunately did add a couple of the trans....185.  packages first.

At first, after a restart hardware drivers also showed 2 in green (activated but not in use)- 173 and current. Deactivated the 173

Hardware drivers screen is still is a bit out of sorts though the 'current' seems to be working fine - screen 2

In any event it is up and running, wil have to compare to the 195 on other partition

---

### Post by SevenMachines on 2010-01-05
alberto is busy beavering away on the nvidia binary releases, his ppa should give some idea what will eventually make it to the repository.

---

### Post by mc4man on 2010-01-08
As an update 
as of today's updates these drivers are working much better
 > doug@doug-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4


> doug@doug-desktop:~$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "NV17 Video Texture"



( with full use of compiz now enabled

---

### Post by phillw on 2010-01-09
Hi, they've been busy with the nvid drivers, the following came via the update email.  I still don't know how long it takes them to hit the reposititries after being accepted, I guess to keep an eye out for the files ..

Just to let you know that the devs aren't ignoring you all :D

Regards,

Phill.

> nvidia-graphics-drivers-173 (173.14.22-0ubuntu1) lucid; urgency=low

  * Rework packaging taking Mandriva's as a model:
    - Use alternatives instead of diversions.
    - Reduce the number of binary packages to nvidia-173,
      nvidia-173-dev and nvidia-173-modaliases.
  * debian/rules:
    - Switch to CDBS.
    - Remove libGL.la as no static library is provided.
  * debian/[nvidia-current.README.Debian.in]("http://nvidia-current.readme.debian.in/") 
:
    - Document the update process.
  * nvidia-current.postinst: try to build the module for the most
    recent kernel in addition to building it for the current kernel
    (LP: #474917).
  * New upstream release (LP: #494166):
   - Add support for xserver 1.7.x.


> Subject: [ubuntu/lucid] nvidia-graphics-drivers-96 96.43.14-0ubuntu1
        (Accepted)
To: [EMAIL="lucid-changes@lists.ubuntu.com"]lucid-changes@lists.ubuntu.com[/EMAIL]
Message-ID:
        <[EMAIL="20100108232517.5200.54319.launchpad@cocoplum.canonical.com"]20100108232517.5200.54319.launchpad@cocoplum.canonical.com[/EMAIL]>
Content-Type: text/plain; charset="utf-8"

nvidia-graphics-drivers-96 (96.43.14-0ubuntu1) lucid; urgency=low

  * Rework packaging taking Mandriva's as a model:
    - Use alternatives instead of diversions.
    - Reduce the number of binary packages to nvidia-96,
      nvidia-96-dev and nvidia-96-modaliases.
  * debian/rules:
    - Switch to CDBS.
    - Remove libGL.la as no static library is provided.
  * debian/[nvidia-current.README.Debian.in]("http://nvidia-current.readme.debian.in/") 
:
    - Document the update process.
  * nvidia-current.postinst: try to build the module for the most
    recent kernel in addition to building it for the current kernel
    (LP: #474917).
  * New upstream release (LP: #494166):
   - Add support for xserver 1.7.x.


 > nvidia-graphics-drivers 190.53-0ubuntu1


> 
Rework packaging taking Mandriva's as a model:
    - Use alternatives instead of diversions.
    - Reduce the number of binary packages to nvidia-current,
      nvidia-current-dev and nvidia-current-modaliases.
  * debian/rules:
    - Switch to CDBS.
    - Remove libGL.la as no static library is provided.
  * debian/[nvidia-current.README.Debian.in]("http://nvidia-current.readme.debian.in/") 
:
    - Document the update process.
  * nvidia-current.postinst: try to build the module for the most
    recent kernel in addition to building it for the current kernel
    (LP: #474917). - Add support for xserver 1.7.x.
   - Added support for the following GPUs:
     o GeForce G102M
     o GeForce GT 220
     o GeForce G210
     o GeForce G210M
     o GeForce GT 230M
     o GeForce GT 240M
     o GeForce GTS 250M
     o GeForce GTS 260M
   - Fixed a bug in the nvidia-settings disclaimer window for the GPU
     Clock Frequencies Coolbits page, such that the "Accept" button is
     selectable when the desktop is so tall that the entire disclaimer
     can be viewed without scrolling.
   - Fixed a recent regression that caused the Xinerama option to not
     be set properly in the X configuration file when saving and
     merging from the nvidia-settings X Server Display Configuration
     page.
   - Fixed a resource leak in VDPAU's blit-based presentation queue.
     This bug limited the number of presentation queue objects that
     could be created and destroyed in a single application instance,
     and hence could limit the number of streams that could be
     displayed and/or the number of iterations of "loop" playback.
   - Fixed a power management regression that prevented some notebooks
     and systems with integrated GeForce 8 and 9 series GPUs from
     suspending.
   - Fixed a regression that caused TV-OUT controls to be unavailable
     on some GeForce 6 and 7 series GPUs.
   - Updated the NVIDIA X driver to allow, on GeForce 8 or greater
     GPUs, more modes to validate on digital display devices whose
     EDIDs report very constrained HorizSync or VertRefresh ranges.
   - Fixed a randomly occuring X server crash caused by the PixmapCache
     option.
   - Increased the allowed amount of overscan compensation from 100 to
     200.
   - On GPUs with VDPAU feature set B, VDPAU's handling of some
     corrupted or incorrectly formatted H.264 and MPEG streams has
     been improved.
   - Fixed a memory allocation problem with pre-GeForce 8 GPUs that
     caused GLX_EXT_texture_from_pixmap clients (e.g., Compiz, KDE 4)
     to display incorrect contents.
   - Modified the installation location and names of internal VDPAU
     libraries to conform to conventions and Debian packaging guidelines.
     New versions of libvdpau expect this layout. Compatibility with old
     versions of libvdpau is maintained with symlinks.
   - Fixed a bug that could cause errors in graphical applications run
     after a previous application using VDPAU and OpenGL. This behaviour
     was observed when running Gwenole Beauchesne's hwdecode-demos
     application.
   - Modified vdpau.h to increment VDPAU_VERSION, to reflect the fact that
     new features have been added in the past. Also, add the new define
     VDPAU_INTERFACE_VERSION.
   - Fixed a periodic temporary hang in the VDPAU blit-based presentation
     queue.
   - Fixed a problem that caused resolution limitations or corruption on
     certain DisplayPort devices such as the Apple 24" Cinema display or
     some DisplayPort to VGA adapters.
   - Disabled the UseEvents option for GeForce 8 series and higher GPUs
     due to a problem that causes occasional short hangs. It will be
     re-enabled when that bug has been tracked down and fixed.
   - VDPAU now allows multiple streams to be decoded at once, without the
     need to set any environment variables.


---

### Post by castrojo on 2010-01-09
> **phillw said:**
> I still don't know how long it takes them to hit the reposititries after being accepted, I guess to keep an eye out for the files ..

[https://launchpad.net/ubuntu/lucid/+queue](https://launchpad.net/ubuntu/lucid/+queue)
[http://launchpad.net/builders](http://launchpad.net/builders)

---

### Post by phillw on 2010-01-09
> **whiprush said:**
> [https://launchpad.net/ubuntu/lucid/+queue](https://launchpad.net/ubuntu/lucid/+queue)


Thanks :D

Phill.

---

