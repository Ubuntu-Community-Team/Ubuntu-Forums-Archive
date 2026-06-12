---
title: "Diskless install over NFS: some &quot;newbie-friendly&quot; assistance?"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by debest on 2008-01-22
I'm attempting to get (k)Ubuntu Gutsy on a diskless (but otherwise modern) PC.  I tried without success to install an old hard drive into the system to help this process (see [this discussion]("http://ubuntuforums.org/showthread.php?p=4175392#post4175392")), so now I'd like to be able to install directly over the network, if possible.  The particulars on the diskless client:[LIST]
[*]Compaq D510 Ultra-slim desktop (PXE compliant, will also boot perfectly from USB)
[*]P4 1.7GHz
[*]1 GB ram
[*]100 Mb Ethernet
[/LIST]Unless I'm mistaken, this should work just fine as a diskless "fat client".  My server is also running Gutsy.

I found the DisklessUbuntuHowto ([https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)), and started trying to follow it.  However, it assumes (and states as such) that I require a good understanding of Linux.  While I'm working on it, I don't yet qualify for that statement :-)

Here is how my setup is going to differ from the author's Howto:
[LIST]
[*]I am using a Linksys WRT54GL (upgraded with DD-WRT firmware) as my DHCP server.  I'm hoping that I can follow the advice in [this discussion on dd-wrt.com]("http://www.dd-wrt.com/phpBB2/viewtopic.php?t=4662") to get PXE working on that box.
[*]As noted above, I am not able to locally install Ubuntu on the client, so I'm just going to try to copy the install of the Ubuntu server to an NFS share on the same machine (if that makes sense).
[/LIST]

So, here's my issues that I don't understand:
[LIST]
[*]About 1/3 of the way down the document, it says to edit the file "/etc/default/tftp-hpa".  I have no such file, but I do have a file called "/etc/default/tftpd-hpa".  Is this the file meant to be referred to?
[*]Just below that, says to start the service by entering "sudo /etc/init.d/tftp-hpa start".  Again, should this be "sudo /etc/init.d/tftpd-hpa start"?
[*]About 2/3 of the way down, it says to copy everything over to the nfs directory.  One of his lines of code is this:```
mount -tnfs -onolock 192.168.1.2:/nfsroot /mnt
```Now, everything else in the Howto is on the 192.168.2.0 subnet: was this another typo (should have been 192.168.2.2), or do I not understand? 
[*]In general, the document seems to be rather randomly laid out, and I'm having difficulty following it when I am unfamiliar with many of the commands.  If I am right about the above and there are typos in the code, how many more are there?
[/LIST]

In summary, is anyone able to help a willing newbie to interpret a document, or perhaps point me toward a more simplified and "spelled-out" guide to follow?  Thanks in advance to all who can help!

---

### Post by debest on 2008-01-24
Sorry to bump, but I'm stuck.  I really don't know what to do when I get to the section on "Creating your NFS installation" of the [DisklessUbuntuHowto]("https://help.ubuntu.com/community/DisklessUbuntuHowto") document.  

I'm confused about the objective of this section.  What is meant to be accomplished by all the steps as they are written?  Why copy the kernel to my home directory?  What is the initrd.img file?  Is all this supposed to be taking place on the "diskless client" or the server?  If it is on the client, I'm SOL since I cannot install Ubuntu to my client (can't get the hard drive recognized).

Anyone been through my pain?  Thanks.

---

### Post by debest on 2008-01-24
One more bump, please.  Has anyone tried to follow this Howto and can give me some help?  Thank you very much.

---

