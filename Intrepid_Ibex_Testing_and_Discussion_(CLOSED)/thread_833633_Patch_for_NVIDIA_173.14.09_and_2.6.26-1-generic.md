---
title: "Patch for NVIDIA 173.14.09 and 2.6.26-1-generic"
date: 2008-06-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Amaranth on 2008-06-18
Here is a patch that makes it possible to build the 173.14.09 kernel module with the 2.6.26-1-generic kernel. Apply it with the following command:```
sh NVIDIA-Linux-x86-173.14.09-pkg1.run --apply-patch xen.patch.txt
```

Afterward run the following:```
sudo sh NVIDIA-Linux-x86-173.14.09-pkg1-custom.run
```

Note that this will have to be reinstalled (and possibly repatched) on every kernel and/or Xorg update.

**Edit:** Also, compiz still works. :)

---

### Post by Zorael on 2008-06-18
The 2.6.**26-1** kernel? Am I missing something? kernel.org shows 2.6.25-7 as the latest stable version and 2.6.26-rc6 as the latest prepatch.

---

### Post by Amaranth on 2008-06-18
No, 2.6.26**-1**. That means it is the first ABI version of our 2.6.26 kernel packages. It it based on the 2.6.26-rc6 upstream kernel.

---

### Post by Zorael on 2008-06-18
Doh, yes, **-1**; typo on my part. Where can this package be found? I don't see it on the updates repositories. Due to hit them soonish?

---

### Post by Amaranth on 2008-06-18
It went into the repositories about 4 days ago. Are you using intrepid? If so, your mirror might be broken. Mine was, that's why it took me 4 days to get this out. :)

---

### Post by Zorael on 2008-06-18
There it is, thanks. :>

---

### Post by autocrosser on 2008-06-18
Hi Travis!!
I'm getting:

dean@linux:~$ sh '/home/dean/NVIDIA-Linux-x86-173.14.05-pkg1.run' --apply-patch xen.patch.txt
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 173.14.05.............................................................................................................................................................................................................................................................................................
patching file usr/src/nv/conftest.sh
patching file usr/src/nv/nv-linux.h
Hunk #2 FAILED at 139.
Hunk #3 succeeded at 712 (offset -10 lines).
Hunk #4 succeeded at 865 (offset -10 lines).
1 out of 4 hunks FAILED -- saving rejects to file usr/src/nv/nv-linux.h.rej
patching file usr/src/nv/nv.c
Hunk #1 succeeded at 2020 (offset -20 lines).
Hunk #2 succeeded at 2032 (offset -20 lines).
Hunk #3 succeeded at 3903 (offset -16 lines).
Hunk #4 succeeded at 4040 (offset -16 lines).
patching file usr/src/nv/os-interface.c
Failed to apply patch file "/home/dean/xen.patch.txt".


I'm not seeing a /usr/src/nv/nv-linux.h.rej file or even a /usr/src/nv folder?

---

### Post by ronacc on 2008-06-18
is the patch for the xen kernel only ? I tried it with 2.6.26-1-generic (x86_64) and ended up back in failsafe graphics mode . the installer (NVIDIA-Linux-x86_64-173.14.09-pkg2.run) pactched ok and the custom.run installed ok , no clue in the installer log , but did not load when I restarted gdm .

---

### Post by autocrosser on 2008-06-18
I looked at the patch & it excludes xen kernels--no idea why I'm getting the error I got--I would guess that your problem has to do with the 64bit issue...

---

### Post by Amaranth on 2008-06-18
I have only tested this on x86 kernels as I have no x86_64 hardware available. Also, this is for the 173.14.09 driver, not the 173.14.05 driver. The latter doesn't even support 2.6.26 kernels.

Also, the regular generic kernel is a xen kernel, they've merged the two together. I dunno if it supports Dom0 or just DomU (I know fedora only supports DomU) but there is some kind of Xen support in there.

---

### Post by ronacc on 2008-06-18
noticed something strange , my xorg.log dosen't show the attempts to start with 173.14.09 , either the patched or unpatched versions , only the sucessful starts with nv and I made sure that I had a known good xorg.conf file for the tries with 173.14.09 .

---

### Post by autocrosser on 2008-06-18
Oops--my bad--I'll get the -09 & report progress.....

---

### Post by autocrosser on 2008-06-18
Well-I tried to do it all--everything looked like it worked. but upon reboot--I was still in low graphics mode--have gave it up for a bad job right now....

Thank you for the good try Travis!!!

---

### Post by ronacc on 2008-06-18
yes thanks for the try  , you did the best you could with what you had to work with .

---

### Post by Amaranth on 2008-06-18
Can you guys attach your /etc/X11/xorg.conf and the /var/log/Xorg.0.log from when you tried to start X with this driver? That would be helpful in seeing what is going on. I just tried this again from scratch and it works perfectly on my GeForce Go 7400.

I was hoping to get better responses, this is the patch I gave to the guys who work on lrm hoping we could get nvidia-glx-new packages again. :(

---

### Post by autocrosser on 2008-06-19
It is a bit late here--I will give it a go tomorrow eve--7/9ish Pacific & report here...nite all!!

---

### Post by plun on 2008-06-19
> **Amaranth said:**
> 
**Edit:** Also, compiz still works. :)

Yes it does....:D

Well, this explains it, I unticked Virtualization for Ubuntus kernel when
I rebuilt it a few days ago (confusion within another thread).


I don get it why a _generic kernel_ should have virtualization :confused:


Nevertheless I checked the patch and used it for the 177.13 driver and "nema problema".

Sidenote, unpacks a driver
```
sudo sh NVIDIA-Linux-x86-177.13-pkg1.run -x
```



(coolbits seems to be broken but I must laborate more)


Thanks !!!

---

### Post by ronacc on 2008-06-19
> **Amaranth said:**
> Can you guys attach your /etc/X11/xorg.conf and the /var/log/Xorg.0.log from when you tried to start X with this driver? That would be helpful in seeing what is going on. I just tried this again from scratch and it works perfectly on my GeForce Go 7400.

I was hoping to get better responses, this is the patch I gave to the guys who work on lrm hoping we could get nvidia-glx-new packages again. :(

here are the logs you requested . the xorg.conf was working with several different versions of the nvidia driver with the 2.6.24-16 kernel . also including the nvidia installer log.

oops had to add a .txt to xorg.conf to get it to attach , the others are too big for that extension I will try zipping them .

---

### Post by ronacc on 2008-06-19
here are the other 2 logs

---

### Post by Amaranth on 2008-06-19
This log is from when you were using the vesa driver. You need to attempt to start X with the nvidia driver, wait for it to fail into bulletproof X mode, then snag the /var/log/Xorg.0.log.old file before doing anything else with X.

---

### Post by ronacc on 2008-06-19
no that is the log from when I attempted to start with the freshly installed patched nvidia driver (custom.run) as I noted a couple of posts above my xorg.log(s) do not even show the attempts to load the nvidia driver either patched or unpatched . 
the way I copied that log was , in intrepid deleted my xorg.conf(NV) and inserted the known good xorg.conf as attached above , shut down gdm (sudo /etc/init.d/gdm stop) , from term installed the custom.run and started gdm (sudo /etc/init.d/gdm start) , when the low graphics warning box appeared I killed it with ctrl>alt>bkspc and from term copied /var/log/xorg.0.log  to my /home for attaching . then adjusted my xorg.conf to use the nv driver and restarted gdm to post the logs.
sorry for being long winded but I wanted you to know exactly how I got what I posted.

---

### Post by Eclipse. on 2008-06-19
Thank you!

Just what I was looking for.;)

---

### Post by plun on 2008-06-19
Fwiw to "ronacc", somewhere I found this :confused: and I am running
this line commented out.

```
sudo gedit /etc/modprobe.d/lrm-video

#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS

```

As I recalls it the reason was if you use a "home-brewed" kernel, maybe its
worth a try ?

---

### Post by ronacc on 2008-06-19
thanks that got it I can now rotate my cube again :lolflag:
@Amaranth  the line plun pointed out in  /etc/modprobe.d/lrm-video was causing the driver not  to load , commenting it out allows your patched driver to work . I wonder why only seems to affect 64bit ?

---

### Post by Eclipse. on 2008-06-19
> **ronacc said:**
> thanks that got it I can now rotate my cube again :lolflag:
@Amaranth  the line plun pointed out in  /etc/modprobe.d/lrm-video was causing the driver not  to load , commenting it out allows your patched driver to work . I wonder why only seems to affect 64bit ?

64bit is not the problem, i had to comment out that line aswell on 32bit.

Everything working great now though.:)

---

### Post by ronacc on 2008-06-19
ok I'll rephrase my question why only some systems , according to the posts it works for some with out having to comment that line , atleast they don't mention it.

---

### Post by plun on 2008-06-19
> **ronacc said:**
> ok I'll rephrase my question why only some systems , according to the posts it works for some with out having to comment that line , atleast they don't mention it.

Well, do we have other confirms about this ?  You, I and Eclipse

I also just saw that there is a new kernel in the build machine...:)
(and a bump for all modules)

and then...  whats a cube  ?  You have probably a **sphere** now....:)

ccsm > cube reflection and deformation > tab deformation > sphere

I am running GIT myself but its probably there...:)

---

### Post by ronacc on 2008-06-19
busy now I'll try the sphere later .

---

### Post by Amaranth on 2008-06-19
You guys apparently still have linux-restricted-modules installed. I only needed it for the nvidia driver so I completely removed it. I guess that explains it.

---

### Post by ronacc on 2008-06-19
@ plun its evening here now so I've got some time to play , the sphere and cylinder are working for me :) though I kinda like the cube , I guess I'm just a square old geezer :lolflag:
@Amaranth yes I've got jockey and lrm installed , when I first installed the 2.6.26-1 kernel and I was trying to get the nvidia driver to load I had purged them but then put them back in when that didn't help .I want to play with getting my rtl-8185 wireless card working and thought I might need lrm for that .

---

### Post by xaenyx on 2008-06-19
I've got a NVidia 6150SE/nForce 430, and am trying to patch the 64 bit driver (NVIDIA-Linux-x86_64-173.14.09-pkg2.run), however whenever I try I get:

```

user@basement-desktop:~/Desktop/nvidia$ ls
NVIDIA-Linux-x86_64-173.14.09-pkg2.run  xen.patch.txt
user@basement-desktop:~/Desktop/nvidia$ sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run --apply-patch xen.patch.txt
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 173.14.09...........................................................................................................................................
Couldn't locate the 'patch' utility.

```

Any idea?

EDIT: Looking at the source of the driver, I see this:

```

if [ $? -eq 0 -a "$patch" ]; then
...
else
  $echo "Couldn't locate the 'patch' utility."
fi

```

EDIT 2: Solved, just needed to sudo apt-get install patch.  Wooo, just rewrote my xorg.conf and everything's swell.

---

### Post by plun on 2008-06-20
> **Amaranth said:**
> You guys apparently still have linux-restricted-modules installed. I only needed it for the nvidia driver so I completely removed it. I guess that explains it.

OK... well I would call that a "bug".


ronacc wrote:
> just a square old geezer 

Okidok....:biggrin:



(My PC started in slow motion this morning but thats probably another issue)

---

### Post by autocrosser on 2008-06-20
I need the restricted-modules 'cause I'm lazy & don't want to make the modules for some of my other stuff that need it----

Seconded on the square ol' geezeer--I had just got my cube to be round--looked cool enough ;)  I'll wait til the repos have the driver (or I'll play with it this weekend if I have enough time) to check out complete roundness:)

---

### Post by plun on 2008-06-20
Just a note that everything works with the new kernel 2.6.26-2

Just installed the patched driver from tty. 

lrm modules are being kept back....:)

---

### Post by cariboo on 2008-06-20
I just got the driver running in intrepid. The biggest problem I had is when I tried modprobe nvidia I got an error saying could not
find /sbin/lrm-video. I just copied lrm-video and lrm-manager from my hardy installation and it worked just fine.

Jim

---

### Post by natros on 2008-06-20
it seems the lrm-video and lrm-manager got removed. 

which package provides the nvidia driver? i can't find it. i can't install apt-file because of unmet dependencies (libapt-pkg-perl). 

for now i'm holding any kernel updates otherwise i'm going to loose the nvidia driver.

thanks

---

### Post by adamorjames on 2008-06-20
Yeah nVIDIA works for me with 2.6.26-2. Next fix would be getting the restricted whatchamacallits so apps can work with nVIDIA. Of course the sound no longer works for me in this kernel but that is a different subject.

---

### Post by autocrosser on 2008-06-21
Amaranth---
As soon as I commented the line that plun noted below, my driver install was alive--I tried installing several times & that was the "fix"

> **plun said:**
> Fwiw to "ronacc", somewhere I found this :confused: and I am running
this line commented out.

```
sudo gedit /etc/modprobe.d/lrm-video

#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS

```As I recalls it the reason was if you use a "home-brewed" kernel, maybe its
worth a try ?

---

### Post by trikloretylen on 2008-06-25
> **adamorjames said:**
> Yeah nVIDIA works for me with 2.6.26-2. Of course the sound no longer works for me in this kernel but that is a different subject.

Perhaps related to this: [http://ubuntuforums.org/showthread.php?t=833825](http://ubuntuforums.org/showthread.php?t=833825)

---

### Post by durand on 2008-06-26
> **plun said:**
> Fwiw to "ronacc", somewhere I found this :confused: and I am running
this line commented out.

```
sudo gedit /etc/modprobe.d/lrm-video

#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS

```

As I recalls it the reason was if you use a "home-brewed" kernel, maybe its
worth a try ?

Thanks a lot!

---

