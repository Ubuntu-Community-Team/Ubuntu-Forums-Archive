---
title: "Installing Ubuntu on a new machine and new HD"
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2015-09-06
I ordered a new desktop machine w/ a new HD that I'm going to use Ubuntu on - no other o/s.

Can somebody give me a link or a procedure for getting this done w/ the least aggravation?

At some point, I'm also going to be copying a lot of files from a Win 8.1 machine to the Ubuntu machine, any advice on the easiest way to do that would also be appreciated.

Thanks

---

### Post by MAFoElffen on 2015-09-06
What kind of PC and HDD? Meaning is the BIOS UEFI?

Once you setup. if you share a file or directory, it will install Samba Client to do SMB sharing. Once that is taken care of... if they were on the same physical network, then you can share what you want on the Windows machine... Connect via SMB through network connections... login with user credentials... then copy over the network. That assumes that you can connect more than one onto your network.

If not, then a network modem cable between the two PC's network cards to do an adhoc network between the two. <-- A lot of people forget you can do this without a network switch. I have a few adapters in my kit that help me convert standard Cat-5 cables to serial/network crossover/modem and sniffer connections.

---

### Post by ra7411 on 2015-09-06
I think I'll simplify things.
If I pull an ntfs HD out of my win8.1 machine, install it in the Ubuntu machine, is Ubuntu going to be able to recognize the various pic, spreadsheet, text, etc files that were created under win8.1?

---

### Post by yancek on 2015-09-06
The link below is a very detailed tutorial on installing Ubuntu.  I don't think it has anything on using UEFI so if you are planning to do that, it won't help much.  It does have a lot of basic information on Linux partitioning and a few links to other tutorials.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

> If I pull an ntfs HD out of my win8.1 machine, install it in the Ubuntu  machine, is Ubuntu going to be able to recognize the various pic,  spreadsheet, text, etc files that were created under win8.1?

You will have to copy the files from windows to Ubuntu using Ubuntu because a default windows system cannot even recognize a Linux filesystem much less read or write to it.  All of the above should work although occasionally there are problems with text files due to line ending in windows.  I guess it depends on which text editor you use in windows.  Post back in a new thread if you have problems after the install.

---

### Post by oldfred on 2015-09-08
Even thought I thought I would not want Windows 8, I shrink it a lot, like to 50GB on 1TB drive. And then ran full backups so I could restore it if needed.
Then installed Ubuntu as main working system, booting in UEFI mode. 
But system was to record TV, but to watch Comcast on demand only Windows worked, so I ended up needing it. :(

I used NFS to link systems and rsync to copy data. I have script to install NFS & default configuration, but had to manually edit IP and paths of folders I was mounting, so ended up mostly manually installing NFS.

---

