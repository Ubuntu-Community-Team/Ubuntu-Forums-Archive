---
title: "Packages installed by fresh Ubuntu 7.04 Server CD (for Amazon EC2)"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by ehammond on 2007-09-12
Summary: How can I find out what packages are installed by default using the Ubuntu 7.04 Feisty server CD?

I have built an Amazon Web Services (AWS) Elastic Compute Cloud (EC2) Amazon Machine Iimage (AMI) for booting an Ubuntu 7.04 Feisty system (contact me if you'd like the public AMI id or instructions for building one yourself).

The barebones system was built using debootstrap which seems to leave many packages uninstalled.

I would like to bring the image up to something comparable to the default set of packages that are installed by the Ubuntu 7.04 Feisty server CD (ubuntu-7.04-server-i386.iso) but I'm not sure how to get that list of packages.

I suppose I could wipe a hard drive, install a fresh copy of Feisty and do
  [FONT="Courier New"]dpkg --get-selections[/FONT]
but I thought there might be an easier way to find this information, perhaps in a file somewhere on the CD image.

I know that the CD installs a few extra packages if you check "LAMP server", but I don't necessarily need those packages in this list.

Any ideas or pointers?

Any other obvious configuration that the install CD does that I might be missing?  debootstrap does a pretty good job and I'm already setting up things like
- /etc/apt/sources.list
- locale
- timezone
- /etc/fstab
- network
- /etc/hosts

**UPDATE: 2007-12-28 Answer Summary**

The main packages for a base Ubuntu can be installed using:
apt-get install ubuntu-standard

A supported Amazon EC2 AMI for Ubuntu 7.04 Feisty: [http://ec2feisty.notlong.com](http://ec2feisty.notlong.com)

A supported Amazon EC2 AMI for Ubuntu 7.10 Gutsy: [http://ec2gutsy.notlong.com](http://ec2gutsy.notlong.com)

---

### Post by ehammond on 2007-10-03
This seemed like a simple question.  Did I confuse things by giving too much project background?

All I want to know is:

   How can I find out what packages are installed by default using the Ubuntu 7.04 Feisty server CD?

Any ideas?

---

### Post by ehammond on 2007-10-03
Based on some research with a feisty server installed using net boot on a kvm virtual machine, it seems that if I simply add the "ubuntu-standard" package to the ones installed by debootstrap then I am very close to the default feisty server install.

  apt-get install ubuntu-standard

This does not include grub, nvidia-kernel-common, and a few other packages, but I don't think I'm going to miss these on Amazon EC2 systems.

---

### Post by jamesdterry on 2007-11-07
I would be most interested in the AMI and/or instructions on how to create it - I'll also try sending a message. TIA!

---

### Post by ehammond on 2007-11-07
Here is the public AMI for my Ubuntu Feisty with a base server install matching the base CD server install as much as possible with a few Amazon EC2 specific tweaks (no fancy application packages installed or running):

    ami-befe1bd7
    level22-ec2-images/ubuntu-feisty-base-20071003a.manifest.xml

Please let me know if you ever start to use this AMI in a serious way (so I don't delete it in a year thinking nobody is using it).

I plan to build an Ubuntu 7.10 base server install image, too.  Let me know if you'd be interested in that.  

Also let me know if you might be interested in subscribing to a mailing list or Google group about Ubuntu on EC2 (or if you know of one).

I have attached some instructions and scripts that I used to build the image (scripts need to have .txt extension removed).

Here is a description of what is in the image:

    - Amazon EC2 AMI tools installed (and patched for Ubuntu) to support bundling the current instance and uploading to Amazon S3.

    - libc6-xen installed for performance

    - /dev/tty[2-6] removed to avoid error messages in logs

    - Comment appended to /etc/motd using /etc/rc.local

    - bootable system built from Ubuntu Feisty (7.04) debootstrap:
      [http://mirrors.kernel.org/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.1~feisty1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.1~feisty1_all.deb)

    - Partitions:
      /    (sda1) 4.0G total, 3.4G available
      /mnt (sda2) as assigned by Amazon EC2 (e.g., 147G)
      swap (sda3) as assigned by Amazon EC2 (e.g., 851M)

    - /etc/apt/sources.list for feisty main restricted universe multiverse

    - Network: DHCP on eth0, loopback on lo, simple /etc/hosts with localhost

    - Amazon EC2 kernel modules installed

    - Shadow passwords enabled

    - root password disabled/locked

    - openssh server installed

    - root ssh public key creditials retrieved from ephemeral store on startup (standard Amazon EC2 ssh access for public AMIs)

    - Added "UseDNS no" to /etc/ssh/sshd_config as recommended by
       [http://docs.amazonwebservices.com/AWSEC2/2007-03-01/DeveloperGuide/public-ami-guidelines.html](http://docs.amazonwebservices.com/AWSEC2/2007-03-01/DeveloperGuide/public-ami-guidelines.html)

    - Locale en_US, Timezone US/Pacific

---

### Post by ehammond on 2007-12-28
Here is a better, upgraded, and supported AMI for Ubuntu 7.04 Feisty:

  [http://ec2feisty.notlong.com](http://ec2feisty.notlong.com)

and one for Ubuntu 7.10 Gutsy:

  [http://ec2gutsy.notlong.com](http://ec2gutsy.notlong.com)

---

### Post by ehammond on 2008-05-08
Another followup since a lot of work has been put into this Ubuntu AMI series for Amazon EC2.  Here is a page summarizing the public AMIs I've made available:

[INDENT][FONT="Courier New"][http://alestic.com](http://alestic.com)[/FONT][/INDENT]

And here is a community around Ubuntu on EC2:

[INDENT][FONT="Courier New"][http://groups.google.com/group/ec2ubuntu](http://groups.google.com/group/ec2ubuntu)[/FONT][/INDENT]

Enjoy!
--
Eric Hammond
[http://www.anvilon.com](http://www.anvilon.com)

---

