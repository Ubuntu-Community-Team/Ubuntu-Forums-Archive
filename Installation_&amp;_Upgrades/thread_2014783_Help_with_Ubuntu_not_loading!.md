---
title: "Help with Ubuntu not loading!"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by foamycaramel on 2012-07-02
I haven't been on my comp in a few weeks and today I tried to boot it up and I got a screen to select which version to load. The options were:

Ubuntu, with Linux 2.6.35-32-generic
Ubuntu, with Linux 2.6.35-32-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)

None of them work.  I'm using aspire revo.  Any help would be greatly appreciated!

---

### Post by darkod on 2012-07-02
Any particular error, when you select the first one for example? It must say something.

---

### Post by lklandaverde on 2012-07-02
hello, im having the same problem, any idea how to fix it?

but when i try with previous linux versions it works, but i have to choose that option....

Please help!!!

---

### Post by lklandaverde on 2012-07-02
> **darkod said:**
> Any particular error, when you select the first one for example? It must say something.

error: couldn read file
Press any key to continue,

then starts a msdos like screen, shows some texts and then freeze,

---

### Post by darkod on 2012-07-02
Boot into live mode with the cd, install boot-repair as explained in the link and run it to do the recommended repair.

If that still doesn't work, make a bootinfo results with boot-repair and post the link it gives you. When we look at the results we might notice something.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by foamycaramel on 2012-07-02
> **darkod said:**
> Any particular error, when you select the first one for example? It must say something.

When I boot into the first one it says:
[0.957538] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
.....some more lines.....
[0.958353] [<c010363e>] kernel_thread_helper+0x6/0x10

If I boot the second, it says the same.

The third just produces a black screen with a flashing cursor.

The fourth produces a lot of lines, the last being:
[4.806647] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k

---

### Post by darkod on 2012-07-02
> **foamycaramel said:**
> When I boot into the first one it says:
[0.957538] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
.....some more lines.....
[0.958353] [<c010363e>] kernel_thread_helper+0x6/0x10

If I boot the second, it says the same.

The third just produces a black screen with a flashing cursor.

The fourth produces a lot of lines, the last being:
[4.806647] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k

Try what I said in post #5. Even if the recommended repair doesn't work, post the bootinfo results link and it should show more details.

---

### Post by foamycaramel on 2012-07-02
> **darkod said:**
> Try what I said in post #5. Even if the recommended repair doesn't work, post the bootinfo results link and it should show more details.

I have a liveUSB but it doesn't seem to be able to read it :/ so can't boot from there

---

### Post by lklandaverde on 2012-07-02
I downloaded the Boot-repair-disk, im running it, hope it works

---

### Post by lklandaverde on 2012-07-02
[http://paste.ubuntu.com/1072273/](http://paste.ubuntu.com/1072273/)
and  still havin same problem

---

### Post by darkod on 2012-07-03
> **lklandaverde said:**
> [http://paste.ubuntu.com/1072273/](http://paste.ubuntu.com/1072273/)
and  still havin same problem

What exactly is the problem? In your case it might be a video issue especially if you are running nvidia.

Have you tried with the nomodeset parameter?

In the grub2 boot menu, highlight the main ubuntu entry, hit 'e' for edit. That will open the boot lines.
Move the cursor to the end of the line starting with linux and after the 'quiet splash' add nomodeset.
Press Ctrl+X to boot. Did that help?

If it did, open Additional Drivers and activate the video driver.

---

### Post by lklandaverde on 2012-07-03
i have added the nomodeset, but still the same
kernel panic - not syncing :VFS : unable to mount root fs on unknown-block(0,0)
pid: 1, comm: swapper/0 not tainted 3.2.0-26-generic #41-ubuntu
call trace:
...
...

---

### Post by lklandaverde on 2012-07-03
i did again all process but nothing change:
paste.ubuntu.com/1073431/

when i start pc it shows a menu with the current version or previous ubuntu versions

if i try with the current starts and shows couldnt read file and gets freeze

but if i try with previous versions works fine

---

### Post by darkod on 2012-07-03
> **lklandaverde said:**
> i did again all process but nothing change:
paste.ubuntu.com/1073431/

when i start pc it shows a menu with the current version or previous ubuntu versions

if i try with the current starts and shows couldnt read file and gets freeze

but if i try with previous versions works fine

Maybe just the latest kernel is corrupted or something, since the previous one is working. According to the script, the latest is 3.2.0-26- and the previous that is working is 3.2.0-25-, right?

You can try removing the latest, and reinstalling it again. Boot the previous one that is working, for example the 3.2.0-25- and in terminal try:
```
sudo apt-get remove --purge linux-image-3.2.0-26-generic
sudo apt-get install linux-image
sudo update-grub
```

That should remove -26- completely and later install it again. And also update grub2 after that.

---

### Post by lklandaverde on 2012-07-03
thnx for the answer, it make some changes, but still with problems.

do i have to edit the boot,

when i start pc reads:

ubuntu, with linux 3.2.0-26-generic-pae
ubuntu, with linux 3.2.0-26-generic-pae (recover mode)
previous linux versions

if i start with the first it says:

cannot read the linux header.
you need to load the kernel first

Press any key to continue...

and then returns to gnu grub menu
and if i try with previous linux 3.2.0-25 works fine?

---

### Post by lklandaverde on 2012-07-03
ok, just a thought:

Im using an IBM Thinkpad T40, is the kernel supported in this CPU?

---

### Post by YannBuntu on 2012-07-04
Hello
> **lklandaverde said:**
> ok, just a thought:

Im using an IBM Thinkpad T40, is the kernel supported in this CPU?

It should.
I think the problem is either a kernel regression, or a kernel incorrectly installed.

Please try this:
```
sudo apt-get purge linux-image-3.2.0-26-generic
sudo apt-get purge linux-headers-3.2.0-26-generic
sudo apt-get purge linux-headers-3.2.0-26
sudo apt-get install linux-image linux-headers-generic
sudo update-grub
```

---

### Post by lklandaverde on 2012-07-04
> **YannBuntu said:**
> Hello


It should.
I think the problem is either a kernel regression, or a kernel incorrectly installed.

Please try this:
```
sudo apt-get purge linux-image-3.2.0-26-generic
sudo apt-get purge linux-headers-3.2.0-26-generic
sudo apt-get purge linux-headers-3.2.0-26
sudo apt-get install linux-image linux-headers-generic
sudo update-grub
```

Thnx for your answer, Im givin'up, doesnt work, still the same problem :(

---

### Post by YannBuntu on 2012-07-04
So it may be a kernel regression.

Please boot on Ubuntu (3.2.0-25 for ex), then type this command:
```
ubuntu-bug linux
```

This will gather information to create a bug report on Launchpad. Then indicate the URL of the bug report please, so that we can follow it.

If you are lucky, you will get a solution from the kernel devs.

---

### Post by lklandaverde on 2012-07-04
> **YannBuntu said:**
> So it may be a kernel regression.

Please boot on Ubuntu (3.2.0-25 for ex), then type this command:
```
ubuntu-bug linux
```

This will gather information to create a bug report on Launchpad. Then indicate the URL of the bug report please, so that we can follow it.

If you are lucky, you will get a solution from the kernel devs.

thnx, do i have to post something here?

---

### Post by YannBuntu on 2012-07-04
Yes: the URL of the bug report please.

---

### Post by lklandaverde on 2012-07-09
ok, this is the link to the bug 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1020998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1020998)

---

