---
title: "Upgrade only one kernel to Jaunty?"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BlueCanary9999 on 2009-04-14
I somehow ended up with two kernels when installing Ubuntu 8.10.  Why, I have no clue, but it's really useful since I messed up one of them (see [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360597") if you think you can help).  Since the problem seems to be with the kernel, I figured updating the kernel (by upgrading to Jaunty) could solve the problem.  But would I be able to upgrade just the problematic kernel to Jaunty and keep the second one with Intrepid?

Another side question, is there a way to "down"-grade to Intrepid if Jaunty doesn't work?

---

### Post by snowpine on 2009-04-14
Nope, upgrading to Jaunty changes a lot more than just the kernel. You would have new versions of practically all of your packages. Plus there is no way to downgrade back to Intrepid.

Simplest solution is use Synaptic to remove the offending kernel, and enjoy the kernel that works. Upgrade to Jaunty if you like (I already have), but not to solve your kernel problem.

---

### Post by snowpine on 2009-04-14
ps I didn't really answer the first part of your question. Each time you install a new kernel (for example when doing a system upgrade), Ubuntu keeps the old kernel too. That way, when you boot the computer, you can choose the old kernel if the new one breaks. You can install older kernels through Synaptics if you wish. I personally like to keep 2 or 3 versions just in case. 

If/when you upgrade to Jaunty, you'll still have the Intrepid kernel(s) too. You can boot your Jaunty system using the old Intrepid kernel if you wish; like I said in my previous post, there is more to each release than just a new kernel.

---

### Post by BlueCanary9999 on 2009-04-14
Ohhh, okay.  Thanks so much for your help!

---

### Post by drs305 on 2009-04-14
You can elect to display the different kernels or not. They are automatically added to the grub menu as they are downloaded. You can also select which kernel you choose to boot, and whether the system boots a new kernel by default. 

There is a good gui app called StartUp-Manager in which you select these and many more options and which will then edit menu.lst for you.

I wrote a guide about using StartUp-Manager and some info on editing menu.lst manually if you choose to do so. See my signature line for the link the the StartUp-Manager (SUM) guide.

---

### Post by BlueCanary9999 on 2009-04-14
>_<  Uninstalling the problematic kernel worked fine.  But it wanted to uninstall linux-generic, linux-image-generic, and linux-restricted-modules-generic with it, since they all seemed to depend on the latest kernel (which I was uninstalling).  So I thought, what the hell, let's see what happens.  And it worked.

But when I saw drs's post, I figured I might as well reinstall all of them and the faulty kernel, and then set the older kernel as the default in grub.  Now... neither will boot.  They get past the "Starting up..." screen, but get stuck on a blank one for 20 minutes until it boots.  V_V  It seems like my attempt to fix the backlight has spread to both kernels, since it increases brightness the right way but the brightness function keys don't.  That's what used to happen on the problematic kernel.

I guess I have another problem.  Just out of curiosity, should I make another topic?

I guess I'll now recklessly try to fix this by uninstalling what was the problematic kernel again and   seeing what happens.....  [EDIT] Yeah, that didn't work.  V_V

---

### Post by BlueCanary9999 on 2009-04-14
(Sorry about the double post.)

The new Jaunty kernel is also problematic.  >_<  The thing is, this isn't a problem with Jaunty.  Thinking about reinstalling Ubuntu completely....

---

