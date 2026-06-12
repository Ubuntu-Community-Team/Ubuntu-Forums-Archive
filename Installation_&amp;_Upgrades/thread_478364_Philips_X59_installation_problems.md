---
title: "Philips X59 installation problems"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by raya28 on 2007-06-19
I am attempting to install Fiesty on my Philips X59, when i use the text install it always hangs at the point of network hardware detection. I am very keen to install can anyone suggest how I can resolve this issue so that I can get a clean install of Ubuntu 7.04.

---

### Post by allebone on 2007-06-23
Hi there

You will have to try a custom made cd that does not include the failing modules. Ubuntu has no inbuilt way of disabling them. Fortunately someone has made such a CD.

[http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm)

Download and install. You will have no wired network though. Only Wireless.

Pete

---

### Post by raya28 on 2007-07-10
Thanks for this, took about two days to BitTorrent the file (no idea?) but have managed to get Ubuntu up and running. However, I now have a different problem which may be due to my move from Windows. 

I have attempted to update Ubuntu once installed (I like to keep everything up to date) but this continually causes Ubuntu to no longer start and therefore require a reinstall. I'm assuming that this is becuase the update replaces the Kernel with the network driver that is not PIO (please don't assume that means I understand very much). Is there some way to tweak Ubuntu so that I can install updates without this happening or do I just have to avoid any Kernel updates from now on?

Any help appreciated.

---

### Post by allebone on 2007-07-21
Unfortunately you cannot update the kernel until the bugs that exist in it are fixed, as you have pointed out, updating the kernel renders your system unusable at the moment.

There are 2 ways to avid the kernel update, while ensuring all other packages are kept up to date. 

The first way is using apt pinning. This can be complicated for a new user but allows greater control over what is held back. There are loads of guides on apt pinning if you are interested in this method.

The second way, which is both easier and probably just as suitable in this specific case is to only run the following command from the CLI (terminal).

Code:
 sudo apt-get update

This will update everything except the kernel. This will have the same effect as apt pinning in this case as the only thing you want to hold back is the dist-upgrades (kernel upgrades).

Using the synaptic manager will run the following command

Code
 sudo apt-get dist-upgrade

Which will break your system. Do not run this command unless you know the bugs that exist with the modules that are causing you problems are fixed.

Pete

---

### Post by allebone on 2007-07-29
Sorry - to clarify in case you do not know this already.

If you update your system and find you can no longer book into Ubuntu, if you press <esc> when booking the pc, when GRUB tels you to press <esc> you can choose the old kernel. That way if you update but it does not work you can still get into your system as Ubuntu does not remove old kernels.

pete

---

### Post by allebone on 2007-07-29
Sorry my k key seems to have mapped differently on this keyboard. I ment boot, obviously

pete

---

### Post by phenest on 2007-07-29
You can fix this problem. I have a Philips X56 with the same problem. If you go to the original site where you downloaded the bittorrent iso, at the bottom of the page is a patch you can download. If you boot into the original kernel, the apply the patch, you will be able to boot into the updated kernel. You should also find the wired ethernet DOES work.

---

