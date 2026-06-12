---
title: "Recent update in synaptic messed up grub"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by TheBlackNoodle on 2006-03-13
I have a dual boot system Ubuntu/Gentoo. They share a boot partition. Ubuntu is my "easy" distro, so I generally just grab updates as they appear. I just got about 7 of them--I'm not sure what they all were. I think about 4 were newish ubuntu sources and one might have been a login manager update.

Anyway, I rebooted my computer and the grub menu was messed up. I had about 15 options (as opposed to my 5 previous) and when I tried to run Ubuntu, it said there was an error with the script. For some reason it also replaced my Gentoo loader's name with "Ubuntu, gentoo-kernel-2.6.15-r7," which is the right information, except it wasn't ubuntu at all.

Fortunately, recovery mode worked and I manually restored my old menu.lst and naming schemes. I also edited grub.conf slightly. It seems like my current setup is fine now, but there's definitely something wrong with that update.

---

### Post by Zelut on 2006-03-13
My guess is that it was the recent kernel update that we all got.  I know kernel updates alter the menu.lst for grub, which could have changed any values that you had entered for using Gentoo.

Glad to hear that you got it fixed.  I wonder if more people have had this problem with kernel updates--conflicts with other boot options.  None of my machines have dual-boots so I haven't run into this issue.

---

### Post by zgerrz on 2006-03-13
I was using InitNG for the latest kernel (2.6.12-10-686-smp) and the kernel update overwrote my settings and I had to manually restore my InitNG configuration in Grub.

In my opinion, the package updater shouldn't modify the Grub file if no new kernels or added. What is the point if the actually kernel version remains the same?

I'm fairly new to Ubuntu, coming from Fedora Core 4. Usually when updates came down the pipeline, it was in the form of a new kernel (new version number as well, even for updates to the same kernel). It was a little confusing to see the same kernel installed again while running apt-get under Ubuntu.

Just thought I'd share my thoughts on something I thought could be improved upon.

---

### Post by DaBruGo on 2006-03-14
[QUOTE=TheBlackNoodle]I have a dual boot system Ubuntu/Gentoo. They share a boot partition. Ubuntu is my "easy" distro, so I generally just grab updates as they appear. I just got about 7 of them--I'm not sure what they all were. I think about 4 were newish ubuntu sources and one might have been a login manager update.

Anyway, I rebooted my computer and the grub menu was messed up. I had about 15 options (as opposed to my 5 previous) and when I tried to run Ubuntu, it said there was an error with the script. For some reason it also replaced my Gentoo loader's name with "Ubuntu, gentoo-kernel-2.6.15-r7," which is the right information, except it wasn't ubuntu at all.

Fortunately, recovery mode worked and I manually restored my old menu.lst and naming schemes. I also edited grub.conf slightly. It seems like my current setup is fine now, but there's definitely something wrong with that update.[/QUOTE]

TheBlackNoodle,

I could be wrong, but I believe the kernel update issue can be resolved (especially for other linux and windows versions you may have in your system) based on where you place your bootup commands in the menu.lst file. If your bootup commands are either above or below a specific section, then nothing ever gets changed for those bootup items in the menu.lst file.

I posted a [LINK]("http://www.ubuntuforums.org/showpost.php?p=774688&postcount=12") in another thread that may fix these issues for you in the future.

Let me know if this helps.


DAVE

---

### Post by TheBlackNoodle on 2006-03-14
Ah, thanks DaBruGo. Useful info there. :)

---

### Post by zgerrz on 2006-03-14
Very nice link, thanks.

This should prevent any future problems regarding Grub being overwritten automatically.

---

