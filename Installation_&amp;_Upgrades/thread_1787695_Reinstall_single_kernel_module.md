---
title: "Reinstall single kernel module"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by BobvanderPoel on 2011-06-21
I'm probably making this harder than it really is ... but, here's what I did.

I noticed that my wacom bamboo tablet wasn't working after I upgraded from 10.10 to 11.04. So, stupidly, I ran the script I had to recompile the wacom.ko module for 10.10. This now creates an invalid module, but installs it in the kernel tree. And, the nice kernel which I _think_ was installed is now gone.

So, I thought I'd be easy to backtrack without doing a complete reinstall. Ummm... what about 

```

 sudo apt-get install --reinstall linux-image

```
Nope. Get the message: The following packages were automatically installed and are no longer required: ...

Now, I'm not sure of what to do next. If I can get the original back I'll ask about the tablet again (I'm pretty sure it wasn't working out of the box.).

Thanks.

---

### Post by Favux on 2011-06-21
You should be able to install linux-image through Synaptic Package Manager.  Just find the right one for your current kernel.  You might want to delete the bad wacom.ko first although the default one should just copy over it.  See Appendix 6 on the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").

---

### Post by BobvanderPoel on 2011-06-21
I thought that synaptic was my friend ... but, no luck.

When I select linux-image I get reinstall grayed out. Same if I try the numbered packages like linux-image-2.6.38-10-generic. However, the package linux-image-2.6.38-8-generic does have a reinstall option.

Of course, on my system the '8' is there and just fine. The problem is with the current image 38-10 which doesn't have a reinstall.

Help ... please ... yup, I'm completely confused.

---

### Post by Favux on 2011-06-21
If entering *uname -r* in a terminal doesn't give enough detail on the kernel use *cat /proc/version_signature* to get the version number you need to be telling Synaptic to use.

---

### Post by BobvanderPoel on 2011-06-21
Ummm, sorry ... I think we might be at different ends on this.

Yes, uname -r, gives me the current kernel:

   2.6.38-10-generic

The problem is that synaptic does not have a reinstall option for this kernel. For other kernels it does. But not the one I need to reinstall.

So, the question I guess is: how do I use synaptic to reinstall a kernel which it doesn't list as reinstallable?

Thanks for taking time to help.

---

### Post by Favux on 2011-06-21
On my current linux-image if I right click on it it offers the option to reinstall it.  You're saying that doesn't exist for you on your current active kernel?  Is it the only Natty kernel you have?

That's sounding like something was broken with install.  As if you got a partial update and so dependencies aren't resolvable.  You'll have to look in Installation and Upgrades for threads about incomplete upgrades/updates or updates hanging.  Basically looking for how to resolve an incomplete update, which you are suppose to be very cautious about allowing to proceed.

---

### Post by BobvanderPoel on 2011-06-22
Solved.

I had at one point enabled the option for pre-released updates. Between having the current kernel installed and now I'd disabled that. So, synaptic/apt could not find the kernel to reinstall.

I could take issue with the error message on this. But life is too short.

Anyway, I enabled the pre-released, reloaded repositories, and reinstalled the kernel. Now I'll have to figure out how to use the tablet!

Thanks.

---

