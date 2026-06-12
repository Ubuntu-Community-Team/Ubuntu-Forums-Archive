---
title: "PPA for nvidia drivers!!!"
date: 2008-07-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-07-06
I was just looking at the current developer's list & this caught my eye!!

<QUOTE>
Message: 9
Date: Sun, 6 Jul 2008 15:01:24 -0700
From: Bryce Harrington [EMAIL="bryce@canonical.com"]<bryce@canonical.com>[/EMAIL]
Subject: Re: 8.04.1 to Intrepid upgrade test
To: [EMAIL="ubuntu-devel@lists.ubuntu.com"]ubuntu-devel@lists.ubuntu.com[/EMAIL]
Message-ID: [EMAIL="20080706220124.GC24849@bryceharrington.org"]<20080706220124.GC24849@bryceharrington.org>[/EMAIL]
Content-Type: text/plain; charset=us-ascii

On Fri, Jul 04, 2008 at 05:55:36PM +0100, Matt Zimmerman wrote:
[INDENT]> With 8.04.1 safely out the door, I decided to brave an upgrade to Intrepid.
> 
>  * Switching to a text console, I found that the reason for the failure was
>    that the nvidia module was missing entirely (LP #243863)
[/INDENT]
We're going to be making some significant changes regarding -nvidia here
coming up.  The driver (along with -fglrx) are going to be broken out of
LRM into standalone packages.  There is also going to be a fourth
version of -nvidia added since nVidia has again broken support for older
hardware.  The naming scheme for the driver will also be changed.  I'll
leave to pitti and tseliot to speak to the particulars since they've
been hot and heavy on this the past few weeks.  Alberto has recently put
a first draft of these changes on his PPA for testing at:
[https://launchpad.net/~lrm-intrepid/+archive]("https://launchpad.net/%7Elrm-intrepid/+archive")

With the current -nvidia in Intrepid, I suspect people have been holding
off on messing with it given the upcoming changes.  I think when the new
stuff gets uploaded we'll see a lot of the current issues resolve.


For bulletproof-x, I'm a bit torn, as it has its uses, but with KDE now
actively deprecating guidance-backends, and our own dropping of
displayconfig-gtk due to its lack of xrandr support, overall it's
exhibiting an increasing number of unaddressed bugs.  Debian's
preference is to instead build an exception-handling capability directly
into the xserver, which is probably a good idea but I've not had time to
look into that, nor have they.  Pending that, I'm wondering if we should
just switch off bulletproof-x mode for now?  The 'xfix' option (which
essentially just does a "dpkg-reconfigure -phigh xserver-xorg") will
cover the case of an invalid xorg.conf; Jockey and Envy-NG are covering
the proprietary module installation/configuration better; other BPX use
cases are largely obsolete with current "config-less" X.org.

Bryce


<END QUOTE>

I am going to take a look at the PPA & download the 177 driver--will report back with findings......

---

### Post by autocrosser on 2008-07-06
OK--I updated my sources & unmodified my /etc/default/linux-restricted-modules-common file. Then selected the "Nvidia-177" driver & source in Synaptic. Had about 20 depends I did not have on the system including exim4? Wondering why a MTA is required for a driver install? 

In any case, all "seems" to be well--rebooted without problem & as I still am using a custom xorg.conf (no "bulletproof x" for me thank you)--GDM loaded & my login "seems" to be a bit quicker that before.....must note that I was already using the 177.13 driver before & am not quite sure if all has gone as planned. Jockey is not reporting the driver, but that might be due to the way it installed--looks like it just automated the normal Nvidia install.

---

### Post by Naddiseo on 2008-07-06
Sweet, I guess I'll attempt II again now nvidia is 'fixed'.

---

### Post by ronacc on 2008-07-06
thankyou for bringing that to our attention . I am happy that the devs are realizing that "failalways"X was a screwup from the word go . There is yet hope for sanity .

---

### Post by autocrosser on 2008-07-06
Bear in mind that this is  Alberto's "test" for a new way to install nvidia drivers--looks kind of like the Envy installer that has been Ubuntu-fied......

Seems to have worked well for me--of course, your mileage may vary ;)

In any case, it's good to see that pitti and tseliot have been burning the midnight oil to make it work\\:D/

---

### Post by autocrosser on 2008-07-06
Yea--"bullethole X" was plain not working for me :(   I was ever so thankful that I have spent so many years writing xorg.conf (and xfree86.conf) files--I still can whip up a go fast enough to get me running ;)

---

### Post by mgsfan on 2008-07-06
tested it 3 minutes ago and rebooted...finally got my screen back..so I'm happy in the time being.

---

### Post by Naddiseo on 2008-07-07
No joy for me, unfortunately. Installed nvidia-glx-177, dumped me into bulletproof-x. Got rid of my custom xorg.conf, rebooted, X started, but using vesa 1024x768 and single monitor. Any suggestions? I'm thinking I did something wrong...

---

### Post by autocrosser on 2008-07-07
Hmmm--I installed Nvidia-glx-177 & the kernel source. You might try 173 (still for the newer cards) or if you card is a bit older use the 96. I do know that they are splitting the drivers up a bit more than before--so your guess could be as good as mine........

Looking at the notes, the 173 is for the 6-7 & 8 series also--might be a safe bet. I've been using the 177 with a 8600GT-OC, so I knew it would work.

---

### Post by plun on 2008-07-07
> **autocrosser said:**
> I was just looking at the current developer's list & this caught my eye!!




Well, Great news....:)

Wait for Xorg or install....:lolflag:


Hopefully its also time for nVidia to join the open source band-wagon.

---

### Post by autocrosser on 2008-07-07
> **plun said:**
> Hopefully its also time for nVidia to join the open source band-wagon.


That would be the best answer--let us see if they really go that way (I am not holding my breath).

---

### Post by plun on 2008-07-07
> **autocrosser said:**
> That would be the best answer--let us see if they really go that way (I am not holding my breath).

Yup.. we will for sure see what happens...

Back to topic...

No problems to install but a total mess with the new xorg :)

Running rescue mode with failsafe driver and downgraded to **Hardys xorg**..  :oops:

nvidia-glx-177 and xserver 1.5  :confused:

Also broken packages for dependencies for 2 virtual packages.

---

### Post by jack482653 on 2008-07-07
> **plun said:**
> Yup.. we will for sure see what happens...


nvidia-glx-177 and xserver 1.5  :confused:

Also broken packages for dependencies for 2 virtual packages.

I can't install nvidia-glx-177 because of  xserver-xorg...:(

> dpkg&#65306;&#34389;&#29702; /var/cache/apt/archives/nvidia-glx-177_177.13-0ubuntu1_i386.deb (--unpack)&#26178;&#20986;&#37679;&#65306;
 &#27491;&#35430;&#22294;&#35206;&#33995;&#8220;/usr/lib/xorg/modules/extensions/libglx.so&#8221;&#65292;&#23427;&#23660;&#26044;&#22871;&#20214; xserver-xorg-core


I have found the solution.Just rename libglx.so.173.14.09 to libglx.so

---

### Post by plun on 2008-07-07
> **jack482653 said:**
> I can't install nvidia-glx-177 because of  xserver-xorg...:(

Nope.. everything seems to be terrible broken but recovery mode
works.

You have no video or input drivers for the moment because they are broken.

The nVidia driver seems to be incompatible with latest xorg.


In recovery mode.

sudo apt-get remove xorg

sudo nano /etc/apt/sources.list

Change i**ntrepid >  hardy**  for main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) *_intrepid_* restricted main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) _*intrepid*_ restricted multiverse universe main #Added by software-properties

sudo apt-get update

sudo apt-get install xorg

sudo /etc/init.d/gdm start

or startx


[B][I]Remember to NOT install anything else from Hardys repo and change
back to Intrepid !!!!
[/I][/B]

Or wait and upgrade from recovery when new packages are available...

Maybe someone else have a smarter solution..:confused:  

:)

---

### Post by Nullack on 2008-07-07
To be clear, Im finding x wont start at all - run level one trying to startx results in server error "X" dir not found.

This isnt an nvidia driver problem but a X issue. No X, no GDM.

---

### Post by plun on 2008-07-07
> **Nullack said:**
> To be clear, Im finding x wont start at all - run level one trying to startx results in server error "X" dir not found.

This isnt an nvidia driver problem but a X issue. No X, no GDM.

Therefore a downgrade is needed for xorg to hardys version as I wrote. A startx gives missing binaries for Intrepids X and
Aptitude shows broken deps which are impossible to solve. 

The nVidia driver is also broken


This is development...:)   Its fixed tomorrow

---

### Post by stari4ek on 2008-07-07
nvidia driver isn't broken.
it works well.
I just didn't update xserver-xorg-core which tries to remove a lot of xserver-xorg stuff.

---

### Post by Nullack on 2008-07-07
yeah :) I see the build que is busy with intrepid xorg server goodness right now

---

### Post by autocrosser on 2008-07-07
I'm avoiding all the new Xorg until it looks like I can install it whilst keeping my 177 driver... I an betting it takes a couple of days for it all to sort out--luck to have drivers just before they are shot to blazes by a Xorg update:roll:

Luck to all--I bet more than a few systems will be on backups tonight.........

---

### Post by ronacc on 2008-07-07
I just updated with aptitude safe-upgrade and it held back the xorg stuff .

---

### Post by autocrosser on 2008-07-07
Yes my friend--I did the same 'bout a hour ago--not feeling adventurous this eve ;)

> **ronacc said:**
> I just updated with aptitude safe-upgrade and it held back the xorg stuff .

---

### Post by plun on 2008-07-08
> **autocrosser said:**
> Yes my friend--I did the same 'bout a hour ago--not feeling adventurous this eve ;)

Well...the nvidia-glx-177 is a adventure. :)

```
plun@dunder:~$ sudo apt-get install nvidia-glx-177
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xfonts-scalable xserver-xorg-video-psb xfonts-75dpi xfonts-100dpi
Use 'apt-get autoremove' to remove them.
Suggested packages:
  nvidia-settings
**The following packages will be REMOVED**
  xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-i810
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-radeonhd
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
The following NEW packages will be installed
  nvidia-glx-177
0 upgraded, 1 newly installed, 47 to remove and 0 not upgraded.
Need to get 0B/8203kB of archives.
After this operation, 7737kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```


Up and running latest Xorg but Alberto must fix his nVidia repo
as I sees it. 

Going to install my custom nVidia driver again but LRM modules was
also changed yesterday  (choosed maintainers config for both)

----------------------------------------

**_Big EDIT_**

--  Lost my tty terminal in normal mode with latest xorg.

--  The custom nVidia driver installs in rescue mode but fails to start.

Maybe this challenge

[http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4](http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4)

------------------------------------------
EDIT again....

Ok to load the custom nVidia driver  (177.13)   :grin:

linux-restricted-modules-common changed again to "nv nv_new" disabling....


Well, this can for sure be a "head banger"....](*,)


O:)

---

### Post by plun on 2008-07-08
Followup about this "head banger"...

Found why "normal mode" and tty was broken after some
log studying.

There is a script within  /etc/init.d/

**nvidia-glx-177**  which wants to start despite
of this package is removed.  



Everything back in normal and excellent performance....:)

---

### Post by tseliot on 2008-07-08
> **plun said:**
> Followup about this "head banger"...

Found why "normal mode" and tty was broken after some
log studying.

There is a script within  /etc/init.d/

**nvidia-glx-177**  which wants to start despite
of this package is removed.  



Everything back in normal and excellent performance....:)

Yes, you should remove that. There's a reason if I haven't released the packages to the public yet...

**EDIT:** I suggest you to wait until Thursday since the packages should be ready for Alpha 2

---

### Post by plun on 2008-07-08
> **tseliot said:**
> Yes, you should remove that. There's a reason if I haven't released the packages to the public yet...

**EDIT:** I suggest you to wait until Thursday since the packages should be ready for Alpha 2

Well..  thanks  !...  your work is much appreciated !!!

This is the most funny part during developments and keeps us from
being transformed to think as "MS slaves"... :)

I also want my freedom and understanding how a OS works and howto manually
install a driver is one issue...

:)

---

### Post by autocrosser on 2008-07-08
Thank you for your hard work!! I will be waiting until Thursday to update Xorg & drivers.


> **tseliot said:**
> Yes, you should remove that. There's a reason if I haven't released the packages to the public yet...

**EDIT:** I suggest you to wait until Thursday since the packages should be ready for Alpha 2

---

### Post by plun on 2008-07-08
> **autocrosser said:**
>  I will be waiting until Thursday to update Xorg & drivers.

To  Thursday....:lolflag:


Well, new drivers are out and works  :)


But... I have rather severe memory leakage...   ~1GB/hour :confused:.

Xorg also constantly around 40% CPU.

---

### Post by autocrosser on 2008-07-08
I must admit you are the adventurous one in the group Plun!!! :):):)

Keep your system going------

---

### Post by Nullack on 2008-07-08
What Nvidia driver is being packaged? Im manually running the 177.13 driver.

---

### Post by autocrosser on 2008-07-08
Two older drivers & the 173 & 177 drivers. I'm running the packaged 177 driver--works out to the same one you are using--just got the second package update for it--looks like he is close to syncing it with the main repo--I would say Thursday is a very good bet.

---

### Post by plun on 2008-07-09
> **autocrosser said:**
> I must admit you are the adventurous one in the group Plun!!! :):):)

Keep your system going------

Well, run the real Debian Sid for a while....:)
Or "punish" yourself with some Gentoo exercise.  :lolflag:


And....  **/home on a separate partition.**


Hardy totally broke one time for me out of any rescue...


"If it breaks it breaks... "  and in 99% of all cases its
easy to fix it ***with the magic terminal***.


Time for tracing my memory leakage...  :-k


EDIT found it...
It was Newton a new experimental Fusion plugin...:tongue:

---

### Post by autocrosser on 2008-07-09
Yes--I've played with Gentoo--Interesting stuff.  I have been partitioning a separate /home for my installs for quite a while--only way to go.

Never tried Deb Sid--been meaning to, just have not made the time.

I've been using the terminal from my UNIX days--still use a term instead of GUI ;)

---

### Post by 3vi1 on 2008-07-13
> **plun said:**
> 
Well, new drivers are out and works  :)


Hmmm.. no luck here:  I don't see nvidia.ko actually being installed anywhere by the nvidia-glx-177 package.

I've tried with and without the LRM packages installed, on the generic kernel.

When I first dist-upgrade from Hardy, I had pretty much the same looking issue with nvidia-glx-new, so had installed a patched 173 manually on the -server kernel, which worked fine (I completely removed all of this before trying the new 177 package on the generic kernel just now).  When doing that manual install: nvidia.ko did definitely get created in the server lib directory.

I'm not even sure where to begin troubleshooting this; there are no errors at all when I install or re-install the 177 package.  :\  Running startx manually dies trying to load nvidia.ko, as modprobing for it show's it's not found (confirmed not there w/locate).

Any gurus have an idea where I can start looking for the problem?  I'd like to find it instead of install clean, in case the cause is something I can file a /bug to avoid problems for other people doing a dist-upgrade.

-J

---

### Post by psyke83 on 2008-07-13
> **3vi1 said:**
> Hmmm.. no luck here:  I don't see nvidia.ko actually being installed anywhere by the nvidia-glx-177 package.

I've tried with and without the LRM packages installed, on the generic kernel.

When I first dist-upgrade from Hardy, I had pretty much the same looking issue with nvidia-glx-new, so had installed a patched 173 manually on the -server kernel, which worked fine (I completely removed all of this before trying the new 177 package on the generic kernel just now).  When doing that manual install: nvidia.ko did definitely get created in the server lib directory.

I'm not even sure where to begin troubleshooting this; there are no errors at all when I install or re-install the 177 package.  :\  Running startx manually dies trying to load nvidia.ko, as modprobing for it show's it's not found (confirmed not there w/locate).

Any gurus have an idea where I can start looking for the problem?  I'd like to find it instead of install clean, in case the cause is something I can file a /bug to avoid problems for other people doing a dist-upgrade.

-J

After the new nvidia-glx-xxx package is installed, run:
```
$ sudo updatedb
``` and ```
$ locate nvidia.ko
```

What's your graphics card model? The -177 driver may not support your card. In that case, remove it and try the nvidia-glx-173 package instead.

---

### Post by plun on 2008-07-13
Well....

I must have this within my xorg.conf

> Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Nothing else  !!!


Its also according to a message about Fedora 9 and Xorg 7.4 within
nVidias forum.

[http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4](http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4)


Identifier name  ????


**tty is also broken for me** in normal mode so its not so fun to fix
it in recovery mode.  Is it working for you, others ????


Still ongoing work withing the lrm ppa.

---

### Post by tseliot on 2008-07-13
> **3vi1 said:**
> Hmmm.. no luck here:  I don't see nvidia.ko actually being installed anywhere by the nvidia-glx-177 package.

I've tried with and without the LRM packages installed, on the generic kernel.

When I first dist-upgrade from Hardy, I had pretty much the same looking issue with nvidia-glx-new, so had installed a patched 173 manually on the -server kernel, which worked fine (I completely removed all of this before trying the new 177 package on the generic kernel just now).  When doing that manual install: nvidia.ko did definitely get created in the server lib directory.
Are you using kernel 2.6.26?

The drivers won't work with 2.6.24.

---

### Post by tseliot on 2008-07-13
> **plun said:**
> 
Identifier name  ????

The identifier is a mere label. Don't worry about it.

---

### Post by plun on 2008-07-13
> **tseliot said:**
> The identifier is a mere label. Don't worry about it.

Thanks...! :)

Can you please confirm if this is correct.

[http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4](http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4)

Then we can skip identifier and only have 
> 
Section "Device"

Driver "nvidia"

EndSection 

within xorg.conf,  the rgb path breaks X if you uses nvidia-xconfig

---

### Post by 3vi1 on 2008-07-13
> **psyke83 said:**
> After the new nvidia-glx-xxx package is installed, run:
```
$ sudo updatedb
``` and ```
$ locate nvidia.ko
```

What's your graphics card model? The -177 driver may not support your card. In that case, remove it and try the nvidia-glx-173 package instead.

Already done, but I appreciate the help - so here goes again:

```
evil@mars:~$ sudo apt-get install --reinstall nvidia-glx-177
[sudo] password for evil:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/8203kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 204165 files and directories currently installed.)
Preparing to replace nvidia-glx-177 177.13-0ubuntu5 (using .../nvidia-glx-177_177.13-0ubuntu5_i386.deb) ...
Unpacking replacement nvidia-glx-177 ...
Processing triggers for man-db ...
Setting up nvidia-glx-177 (177.13-0ubuntu5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
evil@mars:~$ sudo updatedb
evil@mars:~$ locate nvidia.ko
evil@mars:~$

```

My card is a 9600GT - definitely supported by 177.

---

### Post by 3vi1 on 2008-07-13
> **tseliot said:**
> Are you using kernel 2.6.26?

The drivers won't work with 2.6.24.

Yes - I'm trying this with the Kubuntu 2.6.26-3-generic kernel:

```
evil@mars:~$ uname -a
Linux mars 2.6.26-3-generic #1 SMP Wed Jul 2 21:56:15 UTC 2008 i686 GNU/Linux

```

---

### Post by 3vi1 on 2008-07-13
I appreciate the help you guys were attempting to give me - but it looks like I figured it out:

I removed the nvidia-glx-177 package with --purge, and then did an autoremove to be sure things were clean.  I noticed this also did some removal for DKMS.

Then, when I re-installed nvidia-glx-177 it did a step I didn't notice when I first tried to install the driver - adding the module to the dkms system.

Now, the .ko is created properly and works fine!  It's been a long time since I had to fight with video drivers (which says a lot for how good the Ubuntu packages are getting), so I suppose something must have been slightly out of whack with my DKMS configuration before the dist-upgrade.

Thanks again for the assist, guys.

---

### Post by tseliot on 2008-07-14
> **3vi1 said:**
> I appreciate the help you guys were attempting to give me - but it looks like I figured it out:

I removed the nvidia-glx-177 package with --purge, and then did an autoremove to be sure things were clean.  I noticed this also did some removal for DKMS.

Then, when I re-installed nvidia-glx-177 it did a step I didn't notice when I first tried to install the driver - adding the module to the dkms system.

Now, the .ko is created properly and works fine!  It's been a long time since I had to fight with video drivers (which says a lot for how good the Ubuntu packages are getting), so I suppose something must have been slightly out of whack with my DKMS configuration before the dist-upgrade.

Thanks again for the assist, guys.

If you want to recreate the kernel module you will have to install or reinstall the nvidia-<VERSION>-kernel-source (e.g. nvidia-173-kernel-source).

Since you've solved the problem you shouldn't do anything else now.

---

### Post by tseliot on 2008-07-14
> **plun said:**
> Thanks...! :)

Can you please confirm if this is correct.

[http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4](http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4)
Yes, this is correct

> **plun said:**
> Then we can skip identifier and only have within xorg.conf,  the rgb path breaks X if you uses nvidia-xconfig

No, the identifier should stay there since it's used to distinguish one device section from the other.

---

### Post by hugmenot on 2008-07-14
tseliot, I spent some time on the vt tonight after dist-upgrading to Intrepid trying to figure out how the Nvidia building and loading are done by you now.

In the end I got back to Xorg only by issuing 
```
insmod /lib/modules/2.6.26-3-generic/updates/dkms/nvidia.ko
```

"modprobe nvidia" told me nvidia.ko is not found, and just "Xorg" told me the same.

Why is this?

---

### Post by hugmenot on 2008-07-14
Yeah, and one more thing, if you please:

```
Setting up nvidia-common (0.1-0ubuntu9) ...
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 2, in ?
    import NvidiaDetector
ImportError: No module named NvidiaDetector
```

How is this package used, BTW?

---

### Post by tseliot on 2008-07-14
> **hugmenot said:**
> Yeah, and one more thing, if you please:

```
Setting up nvidia-common (0.1-0ubuntu9) ...
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 2, in ?
    import NvidiaDetector
ImportError: No module named NvidiaDetector
```

How is this package used, BTW?
Well, it's not used ;)

type:
sudo apt-get --purge remove nvidia-common

and maybe install revision ubuntu10 (i.e. the latest version).

---

### Post by tseliot on 2008-07-14
> **hugmenot said:**
> tseliot, I spent some time on the vt tonight after dist-upgrading to Intrepid trying to figure out how the Nvidia building and loading are done by you now.

In the end I got back to Xorg only by issuing 
```
insmod /lib/modules/2.6.26-3-generic/updates/dkms/nvidia.ko
```

"modprobe nvidia" told me nvidia.ko is not found, and just "Xorg" told me the same.

Why is this?

Can you attach your /etc/modprobe.d/lrm-video ?

---

### Post by hugmenot on 2008-07-14
```
cat /etc/modprobe.d/lrm-video
# Empty for now

```

*raised eyebrow*

---

### Post by tseliot on 2008-07-14
> **hugmenot said:**
> ```
cat /etc/modprobe.d/lrm-video
# Empty for now

```

*raised eyebrow*

It's ok. What happens if you type:
```
sudo updatedb
```
```
locate nvidia.ko
```

---

### Post by hugmenot on 2008-07-14
Thanks for looking into it, tseliot. These are the locations:

```
$locate nvidia.ko
/lib/modules/2.6.26-3-generic/updates/dkms/nvidia.ko
/var/lib/dkms/nvidia/173.14.09/2.6.26-3-generic/i686/module/nvidia.ko
/var/lib/dkms/nvidia/173.14.09/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia/173.14.09/build/nvidia.ko

```

---

### Post by tseliot on 2008-07-15
> **hugmenot said:**
> Thanks for looking into it, tseliot. These are the locations:

```
$locate nvidia.ko
/lib/modules/2.6.26-3-generic/updates/dkms/nvidia.ko
/var/lib/dkms/nvidia/173.14.09/2.6.26-3-generic/i686/module/nvidia.ko
/var/lib/dkms/nvidia/173.14.09/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia/173.14.09/build/nvidia.ko

```

1) type:
```
sudo depmod -ae
```
```
sudo modprobe nvidia
```
and post the output.

2) if /sbin/lrm-video exists (it shouldn't) please attach its content.

---

### Post by hugmenot on 2008-07-15
So depmod did it, thanks. I think I even had run it after I got X to run and before I posted here; out of a hunch. But I had thought it wouldn't relate to the problem; I&#8217;m terribly ignorant in kernel matters. Now I rebooted and X came up as usual. Funny only that my vt goes black for a minute during bootup.

During the original dist-upgrade there were some bad configure problems due to perl-modules bitching around. Could be it wasn't run then, but I actually added your PPA after the APT system was running as expected again.

So again, grazie ...

---

### Post by autocrosser on 2008-07-16
tseliot--

THANK YOU for all the work you have been doing!!:KS

I just updated to the -4 kernel & watched the new nvidia driver system install without a problem one.......Again, THANK YOU to everyone involved in making the drivers work as well as they do.:guitar:

---

### Post by Danila on 2008-07-16
Hi,
I'm trying to install the nvidia-glx-new-envy driver for my Geforce 7700 Go, but I get the following error from apt:

nvidia-glx-new-envy: depends on: xserver-xorg-core (>= 1:0.99.0-1) but it should not be installed

The message ist translated from German, so it could be different in original...

the installed version of xserver-xorg-core is 1.4.99.905-0ubuntu3

would be happy about any suggestions

---

### Post by litemotiv on 2008-07-16
i got my X back too after manually installing nvidia-glx-177 on kernel .4

things still crippled:

- glx is not found (yet)
- bootup gives the message about the read-only volatile lib dir

---

### Post by lithorus on 2008-07-16
> **Danila said:**
> Hi,
I'm trying to install the nvidia-glx-new-envy driver for my Geforce 7700 Go, but I get the following error from apt:

nvidia-glx-new-envy: depends on: xserver-xorg-core (>= 1:0.99.0-1) but it should not be installed

The message ist translated from German, so it could be different in original...

the installed version of xserver-xorg-core is 1.4.99.905-0ubuntu3

would be happy about any suggestions
Aren't you messing up things here? This thread is not about envy. Envy doesn't work with Interprid either.

---

### Post by autocrosser on 2008-07-16
Please do not use Envy--use the nvidia 177 driver--there is lots of info in this thread & the others about the nvidia changes.

> **Danila said:**
> Hi,
I'm trying to install the nvidia-glx-new-envy driver for my Geforce 7700 Go, but I get the following error from apt:

nvidia-glx-new-envy: depends on: xserver-xorg-core (>= 1:0.99.0-1) but it should not be installed

The message ist translated from German, so it could be different in original...

the installed version of xserver-xorg-core is 1.4.99.905-0ubuntu3

would be happy about any suggestions

---

### Post by tseliot on 2008-07-16
> **Danila said:**
> Hi,
I'm trying to install the nvidia-glx-new-envy driver for my Geforce 7700 Go, but I get the following error from apt:

nvidia-glx-new-envy: depends on: xserver-xorg-core (>= 1:0.99.0-1) but it should not be installed

The message ist translated from German, so it could be different in original...

the installed version of xserver-xorg-core is 1.4.99.905-0ubuntu3

would be happy about any suggestions

type:
```
sudo apt-get install nvidia-glx-173
```

the "-envy" flavours are deprecated in Intrepid.

---

### Post by litemotiv on 2008-07-16
> **litemotiv said:**
> 
- glx is not found (yet)


/usr/lib/xorg/modules/libglx.so symlink wasn't updated to the new version

---

### Post by plun on 2008-07-16
A must read [here]("http://albertomilone.com/wordpress/?p=212") for "nVidia freaks"....

---

### Post by Nullack on 2008-07-16
CUDA support is good. Though Im still waiting for NVIDIA to fix 2d acceleration properly in their Linux drivers.

---

