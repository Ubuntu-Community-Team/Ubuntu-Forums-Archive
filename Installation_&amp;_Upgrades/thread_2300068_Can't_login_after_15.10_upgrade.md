---
title: "Can't login after 15.10 upgrade"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by happyytilton on 2015-10-23
Unable to login to 15.10 after upgrade, nor into the "Guest" session.
Screen goes blank and then returns to the login screen.
It acts as if it's in a loop.
Also "Ctrl+Alt+T" does not bring up the terminal, and the "R" click function does not work either.

System:
Dell E1705 laptop
32bit Dual Core 1.83Hz, 2GB RAM

160GB Dual boot HDD, partitioned as:
C: 30GB-Win XPPro
E: 40GB-XP "My Documents"
F: 20GB-Reflect (Image partition for XP)
V: 10GB-Videos
    47GB-Ubuntu 15.10
      2GB-Swap

---

### Post by kansasnoob on 2015-10-23
According to the tech specs that could have either an Intel or nVidia graphics chip:

[http://www.dell.com/content/topics/topic.aspx/global/products/inspn/topics/en/inspn_e1705_sp_spec?c=us&l=en&s=gen](http://www.dell.com/content/topics/topic.aspx/global/products/inspn/topics/en/inspn_e1705_sp_spec?c=us&l=en&s=gen)

Have you tried booting an older kernel from the advanced boot menu?

If you can boot an older kernel please post the output of:

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

---

### Post by happyytilton on 2015-10-23
[SIZE=2]Sorry, Dell had to replace the original ATI card with: NVIDIA GeForce Go 7900 GS
[/SIZE]
Can boot to older kernel, but have a desktop with no panels showing. Just the 8-10 items on the desktop.
I can pull up the terminal in the old kernel, but that's all.
Very limited as to what can be done, but will try your code and post it back, if I can save it to Windows XP, somehow.
Mind you, everything you have me do, I have to boot back & forth to do them.

---

### Post by Pakkapon_Phongthaw on 2015-10-23
i have same problem with you
Asus A45VM 
I7 3610qm 2.3Ghz
Ram 8GB
Nvidia GT 630m
bad news i already remove old kernel.

---

### Post by kansasnoob on 2015-10-23
I encountered two issues with 15.10 and a slightly different nVidia chip:

Kernel not upgraded during Vivid -> Wily upgrade: 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1508157](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1508157)

Booting live Wily image results in black screen with or without random text

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147)

The latter of the two is not graphics chip specific but jump to comment #10:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147/comments/10](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147/comments/10)

And #11:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147/comments/11](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147/comments/11)

That was an nVidia GeForce 7025 but I found four other nVidia users encountering problems with 15.10:

[http://ubuntuforums.org/showthread.php?t=2299964](http://ubuntuforums.org/showthread.php?t=2299964)

BTW, if you're sure you have an nVidia chip there is really no need to post the output of that command - it would have just provided specific graphics chip info.

---

### Post by happyytilton on 2015-10-23
If memory serves me right, the nVidia driver is v304.125 (it's the one that's "Recommended"), as none of the others worked without locking the system up.

Saving the code was a real bugger, as each and every window opens in the top left corner (covering the previous window) and has NO menu bar, therefore NO way to close it no can you grip it to move it, but after several reboots to get the window opening sequence in proper order, I was able to save the code to the Windows partition.

I read what you said about being sure of the card, but posted the code anyway.
```
hap@MayPop:~$ lspci -v -s `lspci | awk '/VGA/{print $1}'`
01:00.0 VGA compatible controller: NVIDIA Corporation G71M [GeForce Go 7900 GS] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 019b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
    I/O ports at ef00 [size=128]
    [virtual] Expansion ROM at efe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
```

---

### Post by happyytilton on 2015-10-23
Would this have any bearing on my problem?
[http://itsfoss.com/fix-unable-login-ubuntu/?utm_source=newsletter&utm_medium=email&utm_campaign=productivity_tools_and_tips_for_linux_and_other_stories](http://itsfoss.com/fix-unable-login-ubuntu/?utm_source=newsletter&utm_medium=email&utm_campaign=productivity_tools_and_tips_for_linux_and_other_stories)
I had previously upgraded the kernel to 4.0.5 almost 3 months ago with no problems until this 15.10 upgrade.

---

### Post by happyytilton on 2015-10-23
At least with the old kernel, it logs in, but it has no unity, and no launcher, just a few items on the desktop.

---

### Post by happyytilton on 2015-10-23
I figured sooner or later you'd ask which kernels I had, so...
Problematic: 4.0.5-040005 generic
Good one is: 3.19.0-32 generic

---

### Post by kansasnoob on 2015-10-23
> **happyytilton said:**
> Would this have any bearing on my problem?
[http://itsfoss.com/fix-unable-login-ubuntu/?utm_source=newsletter&utm_medium=email&utm_campaign=productivity_tools_and_tips_for_linux_and_other_stories](http://itsfoss.com/fix-unable-login-ubuntu/?utm_source=newsletter&utm_medium=email&utm_campaign=productivity_tools_and_tips_for_linux_and_other_stories)
I had previously upgraded the kernel to 4.0.5 almost 3 months ago with no problems until this 15.10 upgrade.

Seems odd that they're still talking about the 3.19.0.31 kernel on October 9th because Wily is now up to 4.2.0-16 :-k

But if you have 3.19.0-30 or earlier kernels to try it can't hurt anything to try and boot them.

---

### Post by happyytilton on 2015-10-23
The only 2 that I have are:
Problematic: 4.0.5-040005 generic
Good one is: 3.19.0-32 generic

---

### Post by happyytilton on 2015-10-23
The only 2 kernels That I have are:
Problematic: 4.0.5-040005 generic
Good one is: 3.19.0-32 generic

---

### Post by happyytilton on 2015-10-23
I was able to open Firefox through the terminal, but the menu bar is not present so I have no way to minimize Firefox nor am I able to bring focus to the terminal that is now hidden under the Firefox window.
Any suggestions on how to do that.
As of now the only way to get out of the Firefox window is to do a hard shutdown/restart.

---

### Post by happyytilton on 2015-10-23
Figuring that "messed up" is "messed up" and I can't get any worse than a reinstall from the CD, I tried to upgrading the kernel to 4.2.0-17, using this that I had found:
```
sudo add-apt-repository ppa:kernel-ppa
sudo apt-get update
apt-cache showpkg linux-headers
sudo apt-get install linux-headers-4.2.0-17 linux-headers-4.2.0-17-generic linux-image-4.2.0-17generic --fix-missing
```
Then, reboot.

So, now I have a choice of 3 kernels:
3.19.0-32 generic
4.0.5-040005 generic
4.2.0-17 generic

The 3.19.0-32 generic is the only one that will auto-login, but has no launcher, no unity and no menu bar on any window that is open, therefore you can't close them, minimize them, move them, or bring focus to any window that is underneath.
Kernels, 4.0.5-040005 generic and 4.2.0-17 generic, get stuck in a login loop. Even the "Guest" account gets stuck in a login loop.

I have just about learned my lesson on messing with unstable versions and go back to 14.04 LTS. At least everything worked. But NO, I just had to try newer & better!
I'm still hoping someone will come up with workaround or a fix (fingers crossed).

---

### Post by happyytilton on 2015-10-25
I did a reinstall and went back to 14.0.4 LTS.

---

### Post by masterwrks on 2015-10-26
Had same issue. There was error in ```
/var/log/lightdm/x-0.log
``` ```
modprobe: ERROR: could not insert 'nvidia_304': Function not implemented
```
[LIST=1]
[*]I did [installation of nvidia-346]("http://askubuntu.com/questions/564627/startx-fails-could-not-find-module-by-name-nvidia-304") as described, but this has no result after reboot. Also the *4.2.0-17 kernel* was installed during 346 install.
[*]After that I purged Nvidia drivers ```
sudo apt-get purge nvidia*
``` rebooted and was able to login into graphical session - Nouveau driver used. It has worked fine, not so slow and buggy as usual.
[*]But I tried selecting *Nvidia 304.128 tested* in Drivers GUI and after reboot it worked as needed without errors!
[/LIST]

---

### Post by nicholask2 on 2015-11-08
Hi I just wanted to chime in thanking **masterwrks** for his answer and link.

For a couple years I was running 14.04 LTS, then recently upgraded. I had several problems but the last one was that when I tried to boot with kernel 4.20 and log in, the screen would sort of blink, then return me to the log in screen. This happened with all user accounts but did *NOT* happen with kernel 3.19.

I read the link which recommended installing nvidia-346, then read masterwrks's experience, and decided to just blow away my nvidia packages and reboot:

[SIZE=4][FONT=courier new]sudo apt-get purge nvidia-304 nvidia-common nvidia-opencl-icd-304 nvidia-settings
[/FONT][/SIZE]
And that worked for me. I'm now logged in using 15.10. Thank you all for your help. Honestly the function of these drivers is a little foggy to me because I don't even know how the heck my graphics card works at all without any drivers (didn't I just remove them all?), and yet the presence of the drivers is what the problem was.

---

### Post by henpel on 2015-12-07
Hi, 


I have had similar weird issues with 4.2-x kernel and all versions of Nvidia drivers (except the legacy package) + Nouveau driver..

Eventyally with any upgrade i get some weird Nvidia driver originating problems and i guess it's about the K1000M chip i have..

With 4.2.0 kernel and Nouveau driver, lightdm crashed and halted before login screen.

Only working Nvidia driver with 4.2.0 kernel was 304 legacy. I have K1000M (Quadro) chip and problems started after upgrade from 15.04 to 15.10 (several problems in the past..).

Now with 4.2.0 and Nvidia 304 i cannot login, screen flips black and returns to lightdm login screen.

But strange thing was that if i created another user, i was able to login and everything works? This is not real solution but it works and i can login to dig more.

I cannot find any logs providing glues what happens from /var/log/X11, /var/log/* or /var/log/ligthdm.

Tomorrow when back in office i will look again logs if i missed something but i spend half day to try out all nvidia drivers + 3.19.2 + 4.2.0 kernel.

Any advices what to check next or how to debug lightdm more? I'll try trace lightdm if that leads somewhere i have not yet been :)

---

### Post by henpel on 2015-12-08
Argh, the .Xauthority was owned by root after upgrade.

So 'sudo chown myuser:myuser .Xauthority; chmod 0644 .Xauthority' did the trick.

Still i'm having one most likely gtk3 theme. Apps like skype and firefox have weird theme setting, menus, texts and tabs too big and i think it has relation with gtk3.

This looks the same: [https://bugs.launchpad.net/inkscape-devlibs/+bug/1253541](https://bugs.launchpad.net/inkscape-devlibs/+bug/1253541)

---

