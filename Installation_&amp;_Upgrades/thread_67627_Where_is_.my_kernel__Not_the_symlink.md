---
title: "Where is .my kernel?  Not the symlink"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by ububu on 2005-09-20
I am trying to follow the instructions in the README file for upgrading my kernel:  

[B] You can also upgrade between 2.6.xx releases by patching.  Patches are
   distributed in the traditional gzip and the new bzip2 format.  To
   install by patching, get all the newer patch files, enter the
   top level directory of the kernel source (linux-2.6.xx) and execute:

                gzip -cd ../patch-2.6.xx.gz | patch -p1

   or
                bzip2 -dc ../patch-2.6.xx.bz2 | patch -p1[/B]

I don't understand what the "top level of the kernel source" means.  Also, I was doing some housecleaning and  now I see that I probably should not have removed the file named "linux" in the /usr/src directory.  It was a symlink for the kernel (which probably would have told me where the real thing is).  Anyway,I'd like to recreate the symlink and find out where the real kernel is kept so that I can follow the instructions.  Can somebody please explain the instructions with more detail  and tell me how to restore the symlink?  Also, where should I put the kernel patch files before I run the commands to do the patching?  Right now they are on my desktop.  Thank you.

---

### Post by az on 2005-09-20
Had you compiled a kernel from source?  If so, then what is in the /usr/src directory.  Typically, the linux-source-2.6.10 directory would be for the 2.6.10 kernel.

If you did not install your kernel from source, but used a precompiled one, you will not have any kernel in /usr/src.

---

### Post by mlomker on 2005-09-20
My first question is: Why do you think you need to patch the kernel?  Is it because some piece of hardware that you have isn't working or because of something you read somewhere?  Recompiling your own kernel isn't something you want to do unless you are very comfortable with linux.

Look [here](http://www.ubuntuforums.org/showpost.php?p=361253&postcount=10) for instructions on installing the source.

---

### Post by ububu on 2005-09-21
Thank you for your replies.  

I was not aware that patching the kernel was considered recompiling it.  I am following the instructions for setting up the energy saving features of my laptop and they suggest that the kernel be up-to-date in order to get all of the benefits.  The instructions that I am following are as follows:

Configuring the kernel

ACPI (Advanced Configuration and Power Interface) support in the kernel is still work in progress. Using a recent kernel will make sure you'll get the most out of it. 

I already came accross a problem in following the instructions.  My computer has a pentium M processor and the instructions say to configure the kernel like this:

Power Management Options --->
  [*] Power Management Support
  [ ] Software Suspend
  [ ] Suspend-to-Disk Support

  ACPI( Advanced Configuration and Power Interface ) Support --->
    [*] ACPI Support
    [ ]   Sleep States
    [*]   AC Adapter
    [*]   Battery
    <M>   Button
    <M>   Fan
    <M>   Processor
    <M>     Thermal Zone
    < >   ASUS/Medion Laptop Extras
    < >   Toshiba Laptop Extras
    [ ]   Debug Statements
    
  CPU Frequency Scaling --->
    [*] CPU Frequency scaling
          Default CPUFreq governor (userspace)
    <*>   'performance' governor
    <*>   'powersave' governor
    <*>   'ondemand' cpufreq policy governor
    <*>   CPU frequency table helpers
    <M> ACPI Processor P-States driver
    <*> CPUFreq driver for your processor

the last item I could not follow because my processor was not on the list.  I was hoping that if I updated my kernel, it would show up.  The instructions even say:

The kernel has to know how to enable CPU frequency scaling on your processor. As each type of CPU has a different interface, you've got to choose the right driver for your processor. Be careful here - enabling Intel Pentium 4 clock modulation on a Pentium M system will lead to strange results for example. Consult the kernel documentation if you're unsure which one to take.

I am willing to try compiling the kernel at this point because I have nothing on my new comoputer that is important at this point since it is a new computer.  I would rather learn now than later on when that's not the case anymore.  I originally installed the kernel when I installed Ubuntu with their install disc.  I think I have compiled the kernel several times since then though because I have a list of a few options at boot up.

---

### Post by mlomker on 2005-09-21
> I was not aware that patching the kernel was considered recompiling it.

Those actually aren't patches...those are just options that you select when you create the .config file prior to compiling your own kernel.  When you make setting changes like that, you do have to compile a kernel for them to take effect.

> 
ACPI (Advanced Configuration and Power Interface) support in the kernel is still work in progress. Using a recent kernel will make sure you'll get the most out of it. 


The items that you listed are already enabled in Ubuntu's kernel.  I have a brand-new laptop and I use the kernel that came with Ubuntu.

The only time that you need to compile a kernel is if you have really unusual hardware (such as one of the older Compaq laptop with proprietary chips on the system board).  Most modern machine come with a system board from 3 or 4 different companies...talking about generic!  It makes things like this simple, though.

I rather doubt that you've compiled your own kernel.  There are a number of steps to it and if you get a single setting wrong your machine *will not* boot.  I'd say that only half of my custom kernels have even booted.  After what I've learned I steer people away from it, unless they have a very specific need...and even then it is time consuming to get it right.

---

### Post by ububu on 2005-09-21
Thanks again for replying.  The patches that I want to apply are to bring the kernel version from 2.6.5-386 to 2.6.13-386.  Is that considered recompiling the kernel?

---

### Post by mlomker on 2005-09-21
2.6.13 is the latest version.  You cannot apply a patch to Ubuntu's kernel because it already has customized patches.  You'd have to download clean kernel source from [www.kernel.org](www.kernel.org) and then recompile a kernel using all of the proper options.

From what you've said so far, you don't need to do it.

---

### Post by ububu on 2005-09-27
When I downloaded Ubuntu, it installed kernel 2.6.10.  Does Ubuntu have a way of adding in improvements/changes between 2.6.10 and the newest kernel version.  Is there something that I should do to have that happen and if I do uname -a will it always show the original kernel version that was installed with Ubuntu or would it change to the current version?  

also, now when I boot up my computer, I used to get a list to choose from including the one kernel of ubuntu and microsoft windows.  Now I get a list of the "kernel.orig" and "kernel.rej" (or something close to that.  DId I do something wrong and is there something that I can do to get rid or those.  Also, when my computer boots up, it tries to "synchronize" the clock to the ubuntu web server which takes forever if I am not connected to the internet, which is often the case.  Is there some way to stop this from happening.  The network configuration at boot up takes forever too.  Do I really need this to go on or can I take it out of the bootup procedure and take care of it manually?

---

### Post by mlomker on 2005-09-27
[QUOTE=ububu]When I downloaded Ubuntu, it installed kernel 2.6.10.  Does Ubuntu have a way of adding in improvements/changes between 2.6.10 and the newest kernel version.  Is there something that I should do to have that happen and if I do uname -a will it always show the original kernel version that was installed with Ubuntu or would it change to the current version?  
[/quote]

They won't change the kernel version until the next release (Breezy 5.10).  In the interim they send out security updates and that just overwrites the same kernel--it'll have the same uname.

> 
also, now when I boot up my computer, I used to get a list to choose from including the one kernel of ubuntu and microsoft windows.  Now I get a list of the "kernel.orig" and "kernel.rej" (or something close to that.  DId I do something wrong and is there something that I can do to get rid or those.  


You can manually edit /boot/grub/menu.lst but I don't know how it happened.

> 
Also, when my computer boots up, it tries to "synchronize" the clock to the ubuntu web server which takes forever if I am not connected to the internet, which is often the case.  Is there some way to stop this from happening.  


**sudo update-rc.d -f ntpdate remove**

That'll remove the script for ntpdate.

> 
The network configuration at boot up takes forever too.  Do I really need this to go on or can I take it out of the bootup procedure and take care of it manually?

**sudo chmod 600 /etc/hotplug/net.ifup**

That'll prevent hotplug from bringing up the interfaces.

---

### Post by ububu on 2005-09-27
Thank you again for your great replies.  I tried the fix for stopping the network interface set up at bootup, but it didn't work.  It still takes a really long time to run that step of the  boot up.  Do you have another idea?  Here is another question.  When I was figuring out how to get the wireless to work, I ended up with eth2 but I use eth0 for wireless and I'm guessing I'll use eth1 for wired at work, but why did eth2 all of a sudden pop up and can I get rid of it?

---

