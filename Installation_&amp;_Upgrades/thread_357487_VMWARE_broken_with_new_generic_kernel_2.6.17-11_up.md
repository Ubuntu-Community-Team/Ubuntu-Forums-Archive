---
title: "VMWARE broken with new generic kernel 2.6.17-11 update"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by FractalBrain on 2007-02-09
Hey everyone,

So, like some people, I encountered the recent issue of having broken dependencies when upgrading to the new 2.6.17-11 kernel and thus not being able to upgrade via apt-get.  So, today it finally worked and I installed and booted into the new kernel...yay!!

BUT, vmware doesnt work.  I noticed that my vmware had the 2.6.17-10 version kernel installed, so I removed vmware (via apt-get) and tried to reinstall...but vmware-player still wants the 2.6.17-10 version installed....which now it wont do.  Sooo, there is a vmware 2.6.17-11 kernel sitting there, but it doesnt look like I can do anything with it other than look at it and wish I could run vmware.

Anyone have any thoughts on this?  Has anyone else had this problem?  

By the way, I am running kubuntu.  

-Fractal:confused:

---

### Post by rdoolen on 2007-02-09
I have the same problem, on Ubuntu.

---

### Post by Norfolk 'n' Good on 2007-02-09
AHHH!!  Tonight I installed the recent security updates for Edgy and now I can't launch vmware.  Help please, I was in the middle of a university assignment and now I have no access to it!

Thank you

---

### Post by FractalBrain on 2007-02-09
Hey everyone,

I still had my 2.6.17.10 generic kernel, so I booted up into that (instead of my 2.6.17.10) and purged the vmware packages.  I installed vmware-player again (with the 2.6.17.10 kernel version), but had to use apt-get because vmware has a license you have to accept (the GUI doesnt let you enter "ok"...I forgot about that...again).  So, now I am back to the 2.6.17.10 kernel using vmware.  I think I had to do some restarts, but I dont remember the exact sequence.

Maybe that will work for others!   I wonder if it is something we can fix or a repository issue?  

Funny, I was in the middle of an univ assignment as well...and I knew I should hold off on upgrading a kernel...but, but, it was like a big red button that says "dont push"...so I pushed :-)

-Fractal

---

### Post by Invid on 2007-02-10
Hello people,

I just had the same problem and resolved it by reconfiguring VMWare in the terminal. It's fairly simple and can be launched with the command:
```
sudo /usr/bin/vmware-config.pl
```

Apparently there is a module that needs to be rebuilt for the new kernel. I can't remember which one it is, but it will ask you through the config dialogues. For the rest of the options you can just accept the defaults. You'll be back in business in a couple of minutes. 

I am running VMWare Server, but I imagine the issue is the same.

---

### Post by joegiampaoli on 2007-02-10
That is correct, just do:

sudo /usr/bin/vmware-config.pl

Everytime you do a kernel update you must run that command, if you run vmware from shell it will tell you that.

---

### Post by xp_newbie on 2007-02-11
Both Invid and joegiampaoli are correct - just type sudo /usr/bin/vmware-config.pl.

You will be prompted with scaringly looking questions (who remembers which directories I selected the first time when installed vmware?), but don't worry - just hit enter for the suggested default answer and you'll be fine.

I just updated from linux-image 2.6.15-278 to linux-image 2.6.15-28 and went through this without any problem.

---

### Post by rdoolen on 2007-02-11
My vmware works fine if I boot with the 2.6.15.27 kernal but not 2.6.15.28. I tried reconfigurung as described above, but when I try to run vmplayer I get an error that says '/dev/vmmon not found'  (from memeory).

---

### Post by xp_newbie on 2007-02-11
> **rdoolen said:**
> My vmware works fine if I boot with the 2.6.15.27 kernal but not 2.6.15.28. I tried reconfigurung as described above, but when I try to run vmplayer I get an error that says '/dev/vmmon not found'  (from memeory).

Well... when you reconfigured as described above, did you get the following message?

> Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes]
If not, then something is fundamentally flawed in your system.

If yes, you should have responded by hitting 'Enter' ( = [yes] ) and get the following:

> Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-28-686/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.15-28-686/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-686'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-686'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

HTH,
Alex

---

### Post by FractalBrain on 2007-02-12
Hey everyone, thanks for the replys and help!!!!!! 

I only wish I had the  "/usr/bin/vmware-config.pl" to run :) .  Also, when I run vmplayer in the terminal using the command "vmware,"  I get the select your disk to open dialogue, but when I try to open my virtual disk it still doesnt work and I get the message:
"Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded."
I get error messages (at bottom of post) in the terminal when starting vmplayer from the beginning.  It might be important to know that I am running vmplayer version 1.0.2-2. 

My vmplayer works in kernel 2.6.17.10, but I think I get the same messages as the one below.  Anyone think I might not have the vmware-config.pl because I have a newer version?  Could it be calling for GCC 4.2 because it has to rebuild something for the new kernel...or build something having to do with vmware-config.pl...which has something to do with building something for building the new kernel, or perhaps even more something for something else that I don know about?  Isnt that something!  

-FractalBrain
...is pretty fractal right now and wishing he had kernel problems with his corn rather than computer.

```

FractalBrain@offtaskbehavior:/usr/bin$ vmplayer
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:5188): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

(vmplayer:5188): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

---

### Post by xp_newbie on 2007-02-12
FractalBrain, I have no idea how you got VMWare to work in your system in the first place, without the GCC compiler and without the vmware-config.pl.

You certainly got me baffled.

---

### Post by Luggy on 2007-02-12
I don't have vmware-config.pl either and I think it has to do with installing vmware through automatix.

---

### Post by FractalBrain on 2007-02-12
Hi there!!
...well, I fed my computer a nice cup of coffee and it worked!!.  I did some playing around.  My install from apt-get in the 2.6.17-10 OS kernel works just fine.  In the 2.6.17-11 kernel it doesnt work because the preconfigured kernel for vmware will not install, the old 2.6.17-10 version vmware kernel installs instead.  So, when I run in the 2.6.17-11 kernel it doesnt work and it asks for the gcc 4.2 compiler and of course there is no vmware-config.pl script to reconfigure it with.  I uninstalled everything, downloaded the package from the vmware site and ran the install script.  It installed the vmware-config.pl file and everything.  BUT, and I am in the 2.6.17-10 kernel just to make sure I can get it working with the "old" set-up, BUT, it asks for the gcc 4.2 compiler.
Now I am happy I got the new version "installed," but do youses think I need the gcc 4.2 compiler to actually run it?  I mean, it looks like I do, but the 4.2 version has not been officially released yet...I think.
After I get this figured out, then I suppose I will do the vmware-config.pl to get it working on the newer 2.6.17-11 kernel.

Thanks everyone!!!!  Have a super day!

-Fractal

---

### Post by mikewhatever on 2007-04-10
Running sudo /usr/bin/vmware-config.pl probably works if you installed vmware for 2.6.17-10 and now need to reconfigure. It does not, if you try installing with 2.6.17-11
> sudo /usr/bin/vmware-config.pl
sudo: /usr/bin/vmware-config.pl: command not found

Apparently, vmware-player from the repositories does not work on the current kernel version, so the solution for me was to completely uninstall vmware (sudo aptitude purge vmware-player) and use the how to [https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player) to install the latest release from tar ball.

---

### Post by quarky on 2007-04-15
Thanks for that last reply. Fairly confusing that the automatix install doesn't work out of the box for users. Any place we should report this so it can get fixed?

Too me forever to figure out I couldn't use the pre-built version.

---

