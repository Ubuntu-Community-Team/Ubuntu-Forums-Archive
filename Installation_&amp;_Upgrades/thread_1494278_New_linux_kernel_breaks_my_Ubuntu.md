---
title: "New linux kernel breaks my Ubuntu"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by petaloid on 2010-05-26
Every single time I upgrade to linux 2.6.31-22 , my ubuntu breaks.

When I load up ubuntu, I am confronted with a usplash that says "/tmp is not ready yet or not present". I wait for a very long time, and nothing happens.
I hit C to cancel that process, and then it says the same thing about /home. This also stalls and I am unable to make any progress from there.
After cancelling that, it says it can't mount /media/Windows. I skip that as usual. Because I haven't set up the right fstab for automounting windows.
Finally it says my disk has several errors and proceeds to do some checks, without the outward appearance of making progress.

I would let it do it's checks but I have to use my computer before Friday to complete class work.

Is there any quick fix to this problem?
I am running a new installation of Ubuntu (and Windows, which crashed long before this problem with Ubuntu). I partitioned my disk in a manner, with Windows leading, followed by root, swap and then /home, all on their own Primary partitions.
I'm right now talking from my livecd of 10.04. I am about to reinstall ubuntu for the second time, and I would like some advice regarding how to stop the new linux image from breaking my system everytime I upgrade.

---

### Post by sgosnell on 2010-05-26
What version of Ubuntu do you have installed?  For 9.10 on, you can press a Shift key to get a boot menu, and for earlier versions, press Esc.  The menu lets you boot from any installed kernel, and you can boot from your earlier kernel.  That's the quickest fix.  Once you have booted from the older kernel, you can delete the newest one that's giving you problems, through Synaptic package manager.  Just look for linux-kernel, and find 2.6.31-22, mark it for deletion, and then Apply.  Make sure you're booted into a different kernel before doing this, though, and you can do that by typing 'uname -a' in a terminal window.

After that, you might consider installing a later kernel, perhaps 2.6.32 or later.  You can get it [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/) as a .deb file.  Just download the one you want, then open it with gdebi and install it.  If it gives you problems, boot to your current kernel and remove it.  But I think you'll find the later kernels are much more compatible with most hardware, and will probably work better for you.

---

### Post by petaloid on 2010-05-26
I can't do it with previously installed kernels. I am confronted by the same usplash warnings.

---

### Post by petaloid on 2010-05-26
Bump. I could use some help. At least tell me how to prevent Ubuntu from updating to this broken kernel.

---

### Post by sgosnell on 2010-05-26
The update manager lets you choose which packages to update, and which to ignore.  If you install a later kernel, it will remain the default, even if the kernel in the current version is updated.

If you can't boot from previous kernels either, then the problem isn't the kernel, it's a driver.  Are you upgrading to a new version of Ubuntu, not just the normal updates?  If so, you need to update your video driver, most likely.  

The problems finding /tmp and /home are probably the result of bad grub settings.  What is in your fstab file?

---

### Post by petaloid on 2010-06-02
Sorry, I'm back now.

I've figured it out. All my problems are pretty much stemming from a failing hard drive. I am getting this replaced shortly. Now I need some help getting a persistent LiveUSB operational while I flounder to get my HD replaced: [http://ubuntuforums.org/showthread.php?p=9397909#post9397909](http://ubuntuforums.org/showthread.php?p=9397909#post9397909)

Thanks for your help so far.

/closed

---

