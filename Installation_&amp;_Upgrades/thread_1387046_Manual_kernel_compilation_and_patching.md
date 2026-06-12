---
title: "Manual kernel compilation and patching?"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by 00_Spykes on 2010-01-21
Hello there!

In essence, if you don't want to read more than a few lines, this is my question:** I know how to compile a kernel, I know how Grub works, how do I do it all manually without disturbing the installation?** :)

I'm quite happy with my new installation of this Ubuntu Karmic version, aside from a few things (GDM, not being able to unlock a non-root luks partition on boot, etc.). However, this post is about some questions about the Ubuntu kernel and it's patches and theory and whatnot. It's all a bit new to me, as I've more experience with the manual Gentoo way.

Firstly; I've seen many "*How To Compile your own custom kernel*"-threads at this forum, so I wonder if I got the theory right. To put it simply, isn't this the preferred way of doing it or am I forgetting something important:

[LIST=1]
[*]***Make sure you can build the kernel.** (GCC and stuff? Ncurses? Is this packaged in an unbloated bundle somewhere in synaptic?)*
[*]***Get the kernel and put it in /usr/src/.** (Why all the fuss about headers and stuff, what is that anyways? Educate me :) ).*
[*]***make menuconfig; make && make modules_install.** (Or what is the build commands for building the kernel and the modules? Do all distros have their own magic command?)*
[*]***Copy the bzImage to /boot/ and edit the Grub menu to your liking.** Don't overwrite anything that's already there, just do a new entry.*
[/LIST]
So I guess my questions are, is this theory right in Ubuntu too? What is the bare minimum of building blocks you would need? Why headers and patches? Is there something that Ubuntu requires you to have in the kernel (not talking about your hardware, just Ubuntu Karmic)? Is there an unbuilt simple Ubuntu-kernel (or Debian) in the repository so that one wouldn't have to download it from kernel.org?

---

### Post by MaindotC on 2010-01-21
I don't know if this is the OFFICIAL Ubuntu one but you can download .debs of various kernels at [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)  Add the appropriate line to your sources.list and install.

---

### Post by 00_Spykes on 2010-01-22
Hi there strAlan, and thank you for the advice, but I'm afraid I don't really know what I would gain by doing that. I had no idea about PPA's but from what I read it's a form of user-managed debian binary repository?

Hm, this is my scenario; I have multiple operating systems (and multiple kernels on those) on my drives so I already manage a Grub install manually, so that's no problem. I also have no problems configuring a kernel, but it's the compilation and what type of kernel I'm curious about.


[LIST]
[*]Can I compile a kernel from kernel.org with the tools provided by Ubuntu Karmic Koala 9.10 desktop, or do I need to install additional packages, and if so, which ones?
[*]What benefit do I get from running the kernel provided (and updated) by the standard desktop installation of Ubuntu? (Aside from not having to configure and build of course. I'm thinking patches, software, drivers, etc.)
[/LIST]
Hope anyone can help me, have a nice day. :D

---

### Post by MaindotC on 2010-01-22
> **00_Spykes said:**
> I'm afraid I don't really know what I would gain by doing that. 
You would be able to install kernels of your choice without having to do compilation.
> **00_Spykes said:**
> 
[LIST]
[*]Can I compile a kernel from kernel.org with the tools provided by Ubuntu Karmic Koala 9.10 desktop, or do I need to install additional packages, and if so, which ones?
Read the documentation that is associated with each kernel.  It will tell you what dependencies, if any, must be present.  I'm willing to bet you'll need build-essential at the very least.
> [*]What benefit do I get from running the kernel provided (and updated) by the standard desktop installation of Ubuntu?
[/LIST]
The benefits of using a kernel issued with the desktop installation is that is supported by the development team.  If you use a custom or non-stock kernel then you may not be able to receive support from launchpad bug reporting, or all of the millions of other users using the standard installed kernel.

---

### Post by 00_Spykes on 2010-01-22
Hi, and thanks again for helping! :D

> You would be able to install kernels of your choice without having to do compilation.
Yes, but I WANT to compile it myself because I want to have my own configuration. I don't care if I run the same kernel version as Ubuntu does, but I want to have my own **config.** I would even *like* to have the same kernel version because it would save me the trouble of downloading it manually, but alas, the source isn't in the repository is it, because it's a binary distribution? Too bad, the kernel is so important after all...

> The benefits of using a kernel issued with the desktop installation is that is supported by the development team. If you use a custom or non-stock kernel then you may not be able to receive support from launchpad bug reporting, or all of the millions of other users using the standard installed kernel.
Well, yes, but I've never requested such support and after all, what could be more *stock* than the kernel from kernel.org? I mean why would any linux distribution reject that kernel, isn't all kernels based on that one?

Again, thanks for the replies!

---

### Post by MaindotC on 2010-01-22
You are talking about using an unsupported kernel on Ubuntu, and this is clearly a violation of the terms of service and is punishable under court of law.  If you engage in this activity I will have to report this activity to a moderator.

---

### Post by 00_Spykes on 2010-01-23
Oh, oups! Hm, I had... completely forgotten that. Then I absolutely will not do that, phew...

But thank you very much for reminding me. Wow this shocked me, I will definitively read the user agreement more carefully, never thought this would happen in the Linux world. 

Anyhow, perhaps we should ask some moderator to remove this post, because I don't want to be responsible for anyone else to get any law-breaking ideas?

---

### Post by MaindotC on 2010-01-23
Just use the "Edit" button.

---

