---
title: "Disabling secure boot"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by tonma on 2016-09-15
Hello,

I noticed that in the new version of Ubuntu, in order to install important drivers such as wifi drivers, I have no permenantly disable secure boot?
Is that true, or am I missing something? Or I need to disable it just for the installation and then enable it back?

Thanks

---

### Post by Bucky Ball on 2016-09-15
Welcome. Never heard of anything like that. Provide a link if you have one. Secure boot has nothing to do with wireless. It has to do with installing the OS. You have successfully installed Ubuntu? What is the issue? Your wifi is not working?

---

### Post by tonma on 2016-09-15
Hi,
I haven't installed Ubuntu yet. Here is a photo:

[http://imgur.com/KxYeIzE](http://imgur.com/KxYeIzE)

I need to disable the secure boot only for the installation process, and then I can enable it again?

---

### Post by Bucky Ball on 2016-09-15
Leave both of those boxes in the pic unticked and install.

Definitely secure boot off for the install. Not sure why you want to switch secure boot back on again, though. Any particular reason? Basically, its a Windows thing that, yes, can cause all sorts of issues with Ubuntu, including, after a bit of research on my part, if you want to install wireless or video drivers (although this is not always the case). [See post #2 here for more detail]("https://ubuntuforums.org/showthread.php?t=2335620&p=13539065&viewfull=1#post13539065") about what secure boot is and does. There's plenty of other info if you have a quick search.  

I'd leave it off unless you have a specific reason not to. I've personally never used it.

---

### Post by tonma on 2016-09-15
To be honest, my knowledge in OS's is not great. I saw "Secure boot" so that made me think it's something important. I was thinking it's a feature to help prevent any malware to boot the PC up. That's why I thought it should be on, because I will keep using Windows, which is probably more vulnerable than Ubuntu. So you think I should be able to turn it on after installation? Or I will have to keep it off while using Ubuntu?

PS: I just read in many other places that Ubuntu 16.04 and above should not have a problem with secure boot, so why it asks me to turn it off?
   **Also read that is a feature in Ubuntu 16.04, or something like that, just can't understand what they're saying: [http://askubuntu.com/questions/755238/why-disabling-secure-boot-is-enforced-policy-when-installing-3rd-party-modules](http://askubuntu.com/questions/755238/why-disabling-secure-boot-is-enforced-policy-when-installing-3rd-party-modules)

---

### Post by Bucky Ball on 2016-09-15
> **tonma said:**
> To be honest, my knowledge in OS's is not great. I saw "Secure boot" so that made me think it's something important. I was thinking it's a feature to help prevent any malware to boot the PC up.

If you read the link I provided, which perhaps you haven't,it is explained in a quick overview. You might get a few more clues to answer your questions.

Yes, it does prevent malware, if you consider Ubuntu to be malware! Just switch it off, install, switch it back on if you want, switch it off if it prevents you from installing drivers or anything else (although you're going to need to figure out whether its secure boot preventing it if that time comes). 

Like I said, secure boot is an MS thing and consequently, considers anything non-Windows malware. It can prevent you from installing Ubuntu at all.

---

