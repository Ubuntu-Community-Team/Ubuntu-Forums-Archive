---
title: "Mar 10 Alt CD - Installs good, will not boot"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-03-10
I just clean installed the Mar 10 Alternate CD image. The installation ran from start to finish with no hint of any errors, problems, or warnings. I saw the installation do update-grub without problems, too,

When it instructed me to reboot, grub2 gave:

```

error: out of disk
grub rescue>

```So, I booted to a Karmic LiveCD and attempted to reinstall grub. I mounted the Lucid installation partition and chroot'ed to it. When I ran grub-install, it failed with fprot errors. So, I exited back to the LiveCD, umounted the Lucid stuff, and remounted using my Karmic installation. Then, grub-install ran, successfully, but Lucid was not detected. It only gave menu selections for my current and previous Karmic kernels.

A few weeks ago, one gentleman provided me with code for the grub default file to keep selections for Lucid and Lucid recovery mode at the bottom of the grub menu. These have always worked across many deletions and reinstallations of Lucid. Today, they won't work either. If I select either of them, grub says "error: kernel must be loaded first"

So, I got a seemingly perfect installation, but it does not work, at all. What on earth is going on?

Tim

---

### Post by waspbr on 2010-03-10
similar thing happened to me, I used the alternate install CD to attempt a system recovery, The ended up installing all the missing packages.

---

### Post by ratcheer on 2010-03-10
When I attempted to reinstall using the Live CD, I got the same error VMC got:

[http://ubuntuforums.org/showthread.php?t=1426515](http://ubuntuforums.org/showthread.php?t=1426515)

"ubi-partman failed exit code 141"

Tim

---

### Post by ranch hand on 2010-03-10
I would try adding this type of entry to your /etc/grub.d/40_custom file.  This is a symbolic menu entry that just points to the partition and boots the newest debian based kernel it finds.

I use a custom menu with no other entries than these as they never need updated;
```

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF

```
You need to edit the drive partition stuff here to match your box and installation of 10.04.  The stuff between the " marks is what you see in terminal and on the menu.  Can read anything you want.

You need to update your grub of coarse.

I would try this before trying to reinstall as it takes little time and may very well work.  If you get in you may be able to correct the problem.

---

### Post by ratcheer on 2010-03-10
> **ranch hand said:**
> I would try adding this type of entry to your /etc/grub.d/40_custom file.  This is a symbolic menu entry that just points to the partition and boots the newest debian based kernel it finds.

I use a custom menu with no other entries than these as they never need updated;
```

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF

```
You need to edit the drive partition stuff here to match your box and installation of 10.04.  The stuff between the " marks is what you see in terminal and on the menu.  Can read anything you want.

You need to update your grub of coarse.

I would try this before trying to reinstall as it takes little time and may very well work.  If you get in you may be able to correct the problem.

Yes, you are the one who gave me the custom code I referred to in the OP. Thank you, again. I used it, today, and it gave the failure I described: "kernel must be loaded first". Apparently, even though I got a good install on that partition, something about it is totally botched.

Also, the second poster said the same thing happened to him.

Tim

---

### Post by kansasnoob on 2010-03-10
If it's possible to boot that machine with a Live CD please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-03-10
Just BTW it sounds like this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

But I thought that shouldn't happen with Lucid's grub2?

---

### Post by ranch hand on 2010-03-10
I would hang on to the install, myself, as we are getting kernel update regularly.  And try it after the next upgrade.

That is just me and I realize that I have a lot of room to fool with and installs or 10.04 that work.

If I were trying the dailies I would use zsync but also every third or forth day I would do a total new download.  I say that because i had some problems in 9.10-testing where the kernel, for some reason was not always upgraded in zsync.  This may be straightened out now,  I do not know.

I only get the ISO for testing.  Like for the upcoming beta1 release I will be doing a fresh download as that is what folks just coming in will be doing so I have not used zsync this round at all.

---

### Post by ratcheer on 2010-03-10
> **kansasnoob said:**
> If it's possible to boot that machine with a Live CD please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I have already deleted the Lucid install and its partitions. I am ready for whatever comes, tomorrow. Hoping it will be better than what I got, today.

Tim

---

### Post by ratcheer on 2010-03-10
> **ranch hand said:**
> 

If I were trying the dailies I would use zsync but also every third or forth day I would do a total new download.  I say that because i had some problems in 9.10-testing where the kernel, for some reason was not always upgraded in zsync.  This may be straightened out now,  I do not know.



Good idea. I have been zsync'ing this image for a couple of weeks. I have often wondered how they can make sure everything is in there, correctly. However, I assumed that since the checksums were correct, the image content must be correct.

Thanks,
Tim

---

### Post by kansasnoob on 2010-03-10
Todays daily comes out to 718MB, even though it says 685MB, oops! I first thought it was a Zsync problem but it's not.

---

### Post by ratcheer on 2010-03-10
Well, wonder of all wonders! I reinstalled from the LiveCD and instead of the error, it installed. Now, it is back to a normal reboot grinding the disk drive for a long time. But, using the trick of Recovery Mode boot to root prompt to starting gdm gets me up, lickety split. Not perfect, but it gets the job done.

Tim

---

### Post by ratcheer on 2010-03-15
Now, I have installed from the Mar 15 LiveCD image and I cannot get it to boot, at all.

If I try the normal boot method, it completes the fsck in text mode, then it gives me a nice purple Plymouth screen and my disk starts the repeated clicking.

If I try a recovery mode boot, a bunch of text comes onto the screen, then the screen goes black. If I wait, nothing happens. If I press Enter, I get a black screen with an underline cursor at the top of the screen, about 3 inches from the left corner. Then, there are a few of the disk clicks, intermittently. Then, all activity stops. Pressing Enter again has no effect. Nothing can be typed at the underline cursor.

Man, what a pain!

Tim

---

### Post by ratcheer on 2010-03-15
Then, I tried the Mar 15 alternate image. It would not install. It got to the partitioning step and said it could not partition my disk. Then, it messed it up, anyway. When I tried to boot back to Karmic, I got the "out of disk" error, again. I had to boot to the Karmic LiveCD to fix it, again.

Bleh. This is irritating.

Tim

---

