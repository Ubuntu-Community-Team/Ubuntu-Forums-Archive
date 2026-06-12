---
title: "Many upgrades to speed up system"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by jpittack on 2007-10-14
So I am trying to do the monumental task of speeding up everything in my system at once.  This will be long and complicated.  I am open to suggestions on single parts, but would like a unified fix for everything.

Here it goes.

I would like to be upgrading to ATI's driver 8.40.4 and then later, the hyped driver 8.42.x.  Here is the guide I have been following.[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

Next  I want to have the latest kernel.  This is the guide that I will be following.[http://http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel+update]("http://http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel+update")

Next I would like to upgrade to Gutsy.  Beta or not, I do not care.  When I done with all of this, the final release might be out anyways.  I want Compiz Fusion running.

In short, I want the best system with his cheap laptop.

And now for the questions I want to ask the community.

I can not get ATI's driver working under Fiesty's base kernel.  This website proves my theory.
[http://wiki.cchtml.com/index.php/8.40.4]("http://wiki.cchtml.com/index.php/8.40.4").
And the log and output from the terminal from when I foolishly attempt this.
> Build log starting, file:                                                  &#8593; 
 &#9474; /var/cache/modass/fglrx-kernel-src.buildlog.2.6.20-16-generic.1192387322   
 &#9474; Date: Sun, 14 Oct 2007 13:42:02 -0500                                      
 &#9474;                                            
> john@ubuntu:/usr$ sudo module-assistant build fglrx 
The source tarball could not be found! 
Package fglrx-kernel-src not installed? 
Running "m-a -f get fglrx-kernel-src" may help. 
find: /usr/src/modules: No such file or directory 
john@ubuntu:/usr$ 

So I want to know the order I should be going about everything.  Do I upgrade to Gutsy, compile the new kernel, install driver, enable compiz?  Or...do I wait for the new driver and wallow in my 2D desktop until then.

This is the tricky part.  When installing the driver, I need to compile the kernel.  Is the driver compile and the latest kernel compile going to conflict with each other?

And lastly, I will reinstall Fiesty and/or Gutsy as many times as need be.  I have /home on a different partition.

Phew.

I am glad we have this community.  How else would I feed my need for breaking a computer just so I can fix it again?  I promise one day I will know what I am doing.

---

### Post by 5-HT on 2007-10-14
> **jpittack said:**
> 

So I want to know the order I should be going about everything.  Do I upgrade to Gutsy, compile the new kernel, install driver, enable compiz?  Or...do I wait for the new driver and wallow in my 2D desktop until then.

This is the tricky part.  When installing the driver, I need to compile the kernel.  Is the driver compile and the latest kernel compile going to conflict with each other?


From the link you posted, the driver only wouldn't build against 2.6.21. It should build just fine on 2.6.22 and later. Gutsy, as is, and without a custom 2.6.23 will give you fusion. I'm not really sure why you feel like you have to compile a kernel to install the driver though, you just need *a* kernel, custom or not. 

I don't see a reason to wait for a new driver (if it ever comes) to fix the build issues with 2.6.21 as:
1. You can always use the drivers in the repos
2. If you want a custom kernel, just use >2.6.21 and the module will build

It doesn't matter if you upgrade to gutsy before or after rolling your own kernel and ati module- you can use them in feisty or gutsy.

On a related note though, why do you think a custom kernel will be _perceivably_ faster?

cheers,

---

### Post by jpittack on 2007-10-14
> Compile the kernel module:

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

It's necessary, because sometimes this file is written by other packages, and so there's no 3D acceleration. 

I take it I do not know what I am talking about.  I read this as compiling a module that is inside the kernel.

Now that I think about it, the reason that I want to use this custom kernel is so that I don't need to upgrade to Gutsy to see if I can get this driver working.  I have no intent on using the repos, because I was having trouble with that particular driver in Gutsy trying to use compiz.  From what I have been hearing and experiencing, the repos do not include the latest driver, just the one that has been tested and proven stable.  I would rather test the driver myself and take the consequences.

The speed that I am looking for is to come from the ati driver and hopefully, using Gutsy.  I need to use Gutsy as is.  I can unlatch myself from Windows when I can print, scan, set up my e-mail and play video games on Ubuntu.

---

