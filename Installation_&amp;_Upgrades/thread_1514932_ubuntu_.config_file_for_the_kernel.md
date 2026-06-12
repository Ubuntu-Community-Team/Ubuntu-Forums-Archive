---
title: "ubuntu .config file for the kernel"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by schnee123mann on 2010-06-21
Hello,

I'm looking for the .config file for the kernel which ubuntu uses to compile the standard generic kernel which is delivered in compiled form.

I downloaded the following kernel archive ( 2.6.31.8 ):
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=commit;h=047e5f383505cda6606b73d49a857895de5e2c48](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=commit;h=047e5f383505cda6606b73d49a857895de5e2c48)
The archive doesn't contain the .config file.

I need the original file, because I'm not able to configure a working kernel, so I want to try to compile the kernel with the standard configuration. Afterwards I'm going to change some options.

Thank You
Andreas Kasper

---

### Post by odiseo77 on 2010-06-21
It must be inside /usr/src/linux-headers-*-generic (at least it's where it's at in lubuntu); just copy it from there to the sources you want to compile and reconfigure (note that it's a hidden file, so you probably won't see it until you execute ***ls -la*** inside the directory I mentioned before).

Greetings.

---

### Post by schnee123mann on 2010-06-21
hey, thank you for the info ;-)

I have a few more questions:

What is the difference between the two directories:

[LIST]
[*]linux-headers-2.6.32-22
[*]linux-headers-2.6.32-22-generic
[/LIST]
How can I get the .config files for other kernel versions, because I need to patch the kernel to use RTAI and the RTAI patch is only available for certain kernel versions. - Or can I use the config file from a newer kernel version?

Thank you
Andreas Kasper

---

### Post by odiseo77 on 2010-06-21
I'm not sure, but I think you can't use a patch meant for a specific kernel version on a different one. Maybe someone with more experience with kernel issues can helps us better here?

---

### Post by schnee123mann on 2010-06-22
I don't want to patch the kernel with a patch for a wrong version. - I only want to use a .config file from another kernel version, so that I have the correct configuration of the kernel.

---

### Post by odiseo77 on 2010-06-22
hmm, maybe you could use a .config file from an older kernel version to see which options are selected for RTAI, write them down, go back to the kernel you want to compile, and select these options? There could be an easier way to do it, but this is the only one I can think of now.
You can get the .config file from the kernel-headers-{version}-generic package (where {version} is the version of the kernel you want the .config file from). You can download it from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) , so you don't have to install it necessarily.

Greetings.

---

