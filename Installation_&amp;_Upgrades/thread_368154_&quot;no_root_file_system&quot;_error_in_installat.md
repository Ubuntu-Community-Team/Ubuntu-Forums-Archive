---
title: "&quot;no root file system&quot; error in installation"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by feeman_4_life on 2007-02-22
I'm sure this topic has been done to death, but

I get a "no root file system error" when I'm doing an installation.

I am a Linux virgin.

I wiped my 80 hd clean partitioned it in half and gave win xp an install on one partition.  Then I put the cd in, and the partition thing in there, i gave 510mb for a swap and formatted the remaing 39.5 gb (well, 37gb something) into NTFS...

Then on step 5/6, the mounting part, I gave the new partition the "/" thing, assuming that's what I need to do to install ubuntu..... and I just keep getting a bloody "no root file system" error... 

ARGH!.....  I want to give this OS a try, but...  I can't even install it easily.  It's not that I'm not giving ubuntu a chance, it's like ubuntu is not giving me a chance.  What a joke.

What are my options right now to fix this problem? Thank you very much for any help you guys can provide!

---

### Post by mikewhatever on 2007-02-23
So, have you formatted the 37 GB partition allocated for Ubuntu root as ntfs? I think you can't do that, because ntfs is a closed source file system for MS only products. If that's the case, reformat it as ext3.

---

### Post by towsonu2003 on 2007-02-23
have a look at this video: [http://doc.ubuntu.com/screencasts/Installing_Ubuntu_with_Windows_Dual-Boot](http://doc.ubuntu.com/screencasts/Installing_Ubuntu_with_Windows_Dual-Boot)

it tells you how to dual boot. your problem, if you didn't mistype, is due to giving / an NTFS formatted partition. Format your Ubuntu partition as ext3 and it should be fine. 

so you're gonna have:
1 NTFS partition: Windows
1 swap partition
1 ext3 partition: Ubuntu's root ( / )
[optional] 1 ext3 partition: Your home in Ubuntu ( /home )

/ means "root" in Linux (hence "root" filesystem). It's basically the same thing as c: in Windows. Linux cannot be on an NTFS filesystem (because there is no stable write support for it), it prefers a native filesystem such as ext3. Here's detailed info on filesystems in Linux [http://tldp.org/HOWTO/Filesystems-HOWTO.html](http://tldp.org/HOWTO/Filesystems-HOWTO.html)

---

### Post by feeman_4_life on 2007-02-23
Okay, Now it is installing! yay!  Thanks =)

And after this, 

Are there any good very basic Ubuntu primers?  Everything on this site seems comprehensive, but there doesn't seem to be any basic tutorials.

Also, I was wondering, I just actulaly got a brand new computer with the AMD 64 4600+ chip.... is it better off to install the 64version later on, or keep the intell x86 version?

---

### Post by towsonu2003 on 2007-02-23
> **feeman_4_life said:**
> Okay, Now it is installing! yay!  Thanks =)

And after this, 

Are there any good very basic Ubuntu primers?  Everything on this site seems comprehensive, but there doesn't seem to be any basic tutorials.

Also, I was wondering, I just actulaly got a brand new computer with the AMD 64 4600+ chip.... is it better off to install the 64version later on, or keep the intell x86 version?

good primers would be:
[LIST]
[*][http://doc.ubuntu.com/screencasts/](http://doc.ubuntu.com/screencasts/)
[*][http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)
[*][https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[*][http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
[*]of course, the offline documentation in your LiveCD / instlled ubuntu (access using System > Help > System Documentation)
[/LIST]

as per the 64 question, it's a little painful to set up and get going (browser plugins not working etc) so I would use the usual one to get more experience.

---

