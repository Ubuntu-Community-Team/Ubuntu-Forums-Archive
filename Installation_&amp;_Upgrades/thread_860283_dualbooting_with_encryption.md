---
title: "dualbooting with encryption"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by malfist on 2008-07-15
I've been gearing up to reformat my computer because I want to switch when harddrive is the main harddrive (I want to switch the SATA to be the / and /home partitions and the IDE for backup and VM's).
However, I want to enable encryption, and dual boot with XP. Which should I install first, and how should I go about installing it? I want the windows partition protected to.

Can anyone tell me how to do this?

---

### Post by Herman on 2008-07-15
:) Hello malfist,
You can install Ubuntu with the Ubuntu Hardy Heron 'Alternate' CD.

It's normally easier to install Windows XP first and then install Ubuntu after that.

Here is a link about how to install Ubuntu Hardy Heron with full encryption, [Encrypted Ubuntu 8.04 - Step-by-step installation tutorial with screenshots!]("http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml").
Here is a link about how to run the Ubuntu Hardy Heron 'Alternate' CD and dual boot with Windows XP in the same hard disk, [Windows XP + Ubuntu Hardy Heron LTS]("http://users.bigpond.net.au/hermanzone/p3.htm")[COLOR=#000000].[/COLOR]

What did you mean you want the Windows XP partition 'protected'?
If you mean with file encryption I don't know how you can do that, you might need to go buy special software for that, unless you install Windows inside Ubuntu in VMware, 
[HowTo: Windows (XP) on Ubuntu with VMWare Server - Ubuntu Forums]("http://www.google.com.au/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D183209&ei=AvN8SO-9BZqMtwPz5LXQDw&usg=AFQjCNEOYHEHA5QsEdC3JdOkrk0wwkMa1g&sig2=uN_gAjnQY8W0C7YlmCuh8g").
If that's what you mean then you have to install Ubuntu first and then install Windows inside it. That would probably give you the best 'protection' for Windows XP, but it's something a little different than dual booting.

Regards, Herman :)

---

### Post by Herman on 2008-07-15
If you want to dual boot Ubuntu and Windows XP in the normal way, you can protect Windows XP by not using it,  use Ubuntu instead.
All Windows operating systems are weak and vulnerable by design, and are not really safe to use on the internet except for Windows update and a few other 'trusted' sites maybe.
You should use Ubuntu for all your web browsing and sending/receiving email and so on, so that your Windows XP will not be exposed to the internet, thus saving your Windows XP for whatever it is you really need it for. 
If you cannot avoid using Windows XP on the internet, (maybe you need to run some special software for business purposes that only runs on Windows XP and you're not a programmer so you can't make your own program for Ubuntu), then at least make a Partimage backup of your Windows XP after it's all set up and before you expose it to the internet. [Use PartImage]("http://www.psychocats.net/ubuntu/partimage") - by aysiu.
At least then you can quickly revert Windows XP to the way you had it all set up and tweaked the way you like it in a few minutes instead of a few days. whenever it does get infected by any of the hundreds of new viruses that are discovered for it every month.
Nothing can protect Windows XP, but you can back it up and restore it.

---

### Post by malfist on 2008-07-15
I've used linux for the past 3 years (ubuntu off and on), I know the dangers of windows :P. 

I almost never boot into windows, only when I'm in a rare gaming mood, like now. :P I don't use it for anything else.

I don't like VMware, it's clunky and hard to use (from my experence) and I use VirtualBox isntead. However, virtualbox will only allow the guest OS to use one of the cores on my quadcore (however, if it was a dual core it could use both :( ). I usually use the VM for programming in VB (ick) or doing some of the C stuff that is windows only. Wine doesn't like Dev-C++, it doesn't display right.

I don't think I was clear enough with my post.
I want to install windows,
then I want to install ubuntu with full drive encryption, including the windows partition. Is this possible or will I have to use something like truecrypt and have a decrypted boot partition?

---

### Post by Herman on 2008-07-16
> I want to install windows,
then I want to install ubuntu with full drive encryption, including the windows partition. Is this possible or will I have to use something like truecrypt and have a decrypted boot partition?I'm typing to you now from an encrypted Hardy Heron installation, it has a 243.1 MiB /boot partition, ext3, (not encrypted, just plain ext3), and it's in a second hard disk.
The first hard disk has Windows XP Professional, Ubuntu Gutsy Gibbon and Ubuntu Hardy Heron.

I installed this encrypted installation last, and Ubuntu only encrypts it's own / (root) file system, I have Ubuntu installed in one / (root partition. I imagine if I had a separate /home for Ubuntu it would have encrypted that too, but I'm not sure, I haven't that tried out. I wouldn't expect Ubuntu to offer and options to encrypot Windows XP, or even other Ubuntu installations. I don't imagine that wouild be feasible. I think you would need to use some other software if you want to encrypt Windows. I don't know anything about that, and I wonder if it the Ubuntu installer's partitioner would still resize it, I don't think so. I think you would need to make your Windows partition the desired size first, then install Windows and do whatever is needed to encrypt that, then install Ubuntu encrypted afterwards, in the free space. 
I don't know anything about booting an encrypted Windows installation from GRUB. I imagine it would probably still boot the same because the boot sector comes before the file system blocks..

Although this installation I'm typing from is a few weeks old, I haven't used it much, it's just in a spare computer. 
I can tell you that the encrypted Ubuntu operating system only boots via it's own /boot partition, and not by any other GRUB.. Mine has it's own GRUB installed to the MBR of hard disk 2, so I just chainload that from my other GRUB in hard disk 1..
This partition shows up as 'unknown', with a black rectangle around it even in it's own Gnome Partition Editor.

---

### Post by malfist on 2008-07-16
I hate ext3, it's slow, will ubuntu be able to encrypt a JFS partition? I have both a / and a /home, I don't think that would make much of a difference though. I have two harddrives, I may just install windows on the IDE one and ubuntu on the SATA one, I gues I could buy a third HDD for backup instead of a new case.
What tool does ubuntu use to encrypt it? I've got a friend who's an encryption nazi, I'll talk to him and see what he thinks. But I have to wait untill I get my motherboard in because that computer has enigmail set up with thunderbird and he won't open unencrypted e-mails :(
Thanks for your help!

---

### Post by Herman on 2008-07-17
> I hate ext3, it's slow, will ubuntu be able to encrypt a JFS partition? I have both a / and a /home, I don't think that would make much of a difference though. Maybe but I only know how to use the Ubuntu 'Alternate' CD's installer to set up the encrypted file system(s) in 'guided' mode which is pretty much automatic and gave me ext3, which is my favorite anyway. I haven't tried JFS, maybe I'm missing something.
> I have two harddrives, I may just install windows on the IDE one and ubuntu on the SATA one, I gues I could buy a third HDD for backup instead of a new case.:) Okay.
> What tool does ubuntu use to encrypt it? I've got a friend who's an encryption nazi, I'll talk to him and see what he thinks. But I have to wait untill I get my motherboard in because that computer has enigmail set up with thunderbird and he won't open unencrypted e-mails :sad:Here are two links, _[Encrypt devices using dm-crypt and LUKS]("http://www.google.com.au/url?sa=t&ct=res&cd=9&url=http%3A%2F%2Fwww.g-loaded.eu%2F2005%2F11%2F10%2Fencrypt-devices-using-dm-crypt-and-luks%2F&ei=qPR-SMSlBpGqsAPjicC3CQ&usg=AFQjCNFbfBmYHOifErQzUJmpA0ete2zfHQ&sig2=egWJ8GSh6_cehJTwF5iVYA")_, and  _[LUKS - Linux Unified Key Setup]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fluks.endorphin.org%2F&ei=qPR-SMSlBpGqsAPjicC3CQ&usg=AFQjCNHS_gwN3s8BUmZr1oqmNmcii6h3Fg&sig2=IyI-C9o9SUutXfy9VXxXOg")_.

Ubuntu Hardy Heron also comes with Seahorse installed as standard as well, so we can all easily encrypt/decrypt individual files from our righty-click menu and send/receive encrypoted email as soon as we set Seahorse up, regardless of whether or not the rest of the file system is also encrypted or not. I'd think you'd be extremely safe if you had an encrypted file system and used PGP as well!
Here's a link to my how-to on Seahorse, 
[Set up Seahorse]("http://users.bigpond.net.au/hermanzone/p5.htm#Install_Seahorse") - encrypt sensitive files for greater security, send encrypted email  

Regards, Herman :)

---

### Post by malfist on 2008-07-18
Oh I can set up enigmail and send PGP encryped emails on my lappy, but I don't have my keys which is on my harddrive on the computer without a motherboard. I use CryptKeeper which I believe uses dm-crypt to encrypt some folders but that isn't seemless.

Really, I don't have much need for encryption. I'm not hiding anything. I want it for the principal. I believe everyone should use encryption. That would cause two things, one: security, and two: data backups. Plus if you only encrypt when your guilty then ecryption is evidence of guilt. It shouldn't be that way.

I think you for your help. I may do the multi-disk stuff. I can get a 500GB SATA300 without to much of a problem.

Malfist

---

