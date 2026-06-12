---
title: "Encrypted install won't boot ... possible to load onto another system?"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by David Tomic on 2009-03-25
Hi everyone,

*Looooooong*story short, I've installed a copy of Jaunty 9.04 using full disk encryption, and now the LILO boot loader has become corrupted and won't load the system.  I just get the famous "L 99 99 99 ... 99" error message, but that's a story for another thread!

What I'm wondering right now though, is assuming that it's ***just*** LILO that's having problems [and my actual [encrypted] data is still fine], is there ANY way that I can take that drive out of the system, and load it into another [working] OS, so that I can decrypt the contents and copy some of the files onto another disk?

[Obviously I still know the decryption key etc, so that part isn't an issue.]

I'm going to be REALLY bummed if I can't get some of these files back, so any help/suggestions would be **greatly** appreciated!

Thanks a lot!

--David

---

### Post by TheFinePrint on 2009-03-25
I don't think it should be any problem.  I used to run Debian Etch encrypted off of an 80GB drive, and I am fairly certain that I mounted it in my new - encrypted 8.04 LTS - system.

Also you can mount it with the recovery/boot/(whatever you call it)-CD and can transfer your files over network that way.  You might even be able to fix Lilo, although that is not my field.

---

### Post by David Tomic on 2009-03-25
> **TheFinePrint said:**
> I don't think it should be any problem.  I used to run Debian Etch encrypted off of an 80GB drive, and I am fairly certain that I mounted it in my new - encrypted 8.04 LTS - system.

Also you can mount it with the recovery/boot/(whatever you call it)-CD and can transfer your files over network that way.  You might even be able to fix Lilo, although that is not my field.

Okay ... so let's assume that I don't have a clue what I'm doing [because that's pretty close to truth :p], how do I actually mount/decrypt that drive within another system?

---

### Post by TheFinePrint on 2009-03-25
I will assume that you have removed the hard drive, and not used the live CD as a boot CD (because then it will detect the LUKS-partition and prompt for your password).  Instead you have moved the drive over to a new working computer also with Ubuntu, or a compatible Linux-distro.

Figure out what drive name your old drive has.  E.g. do:
```
$ sudo blkid /dev/sdd
  /dev/sdd: UUID=".........................." TYPE="crypt_LUKS"
```

This will work if the entire drive is of type LUKS. For the boot-drive this is usually **not** the case.  Instead you must do:
```
$ sudo blkid /dev/sda**5**
  /dev/sda5: UUID="...................." TYPE="crypt_LUKS"

```

Note that I'm probing the partition, instead of the drive (one character difference).




Go through various drive names and partitions until you find it (an educated guess will do this in no time at all).


Then, to actually  mount the drive do the following (assuming that your drive is **/dev/sdb5** ):
```
$ sudo cryptsetup luksOpen /dev/sdb5 mybrokendrive
  Enter LUKS passphrase
  Command successful.
```

Good.  Now the crypt-part is open.

Usually there is an LVM under the crypt-part.  You open this by doing:

```
$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "storageVG" using metadata type lvm2
  Found volume group "somename" using metadata type lvm2
```

In this case storageVG is my own creation, and somename is my root volume group.  Yours will probably be named somehting else, but I'll use **somename** for now.

```

$ sudo vgchange -a y somename

$ sudo lvscan
  ACTIVE            '/dev/somename/swap_1' [5,90 GB] inherit
  ACTIVE            '/dev/somename/logfiles' [4,82 GB] inherit
  ACTIVE            '/dev/somename/root' [65,00 GB] inherit
  ACTIVE            '/dev/somename/homes' [389,80 GB] inherit

```

This will probably be different in your case, and some of then may list as being inactive.  If this is the case then do:

```
$ sudo lvchange -a y /dev/somename/root
```

Finally, you can mount the logial volume to some temporary location, e.g.

```
$ sudo mount /dev/somename/root /mnt/phew_i_made_it_this_time
```

Of course the location must exist prior to doing **sudo mount**.




Do tell how this turns out.

---

### Post by David Tomic on 2009-04-04
> **TheFinePrint said:**
> ]
Do tell how this turns out.

WOW ... thanks a lot for all of that!

First of all, sorry about the late reply, but today's the first day that I've actually had a chance to sit down and take a proper look at all of this.

So ... with just a little bit of trial and error, I've managed to get the drive mounted on another system - which is terrific  - **BUT** ... I'm afraid that I've run into *another* problem during the process. :(:(

90% of  what I'm after is in the /home folder on the other drive, and I still *can't* access that, because Jaunty has encrypted that separately to the rest of the drive.

IE - During installation you get prompted whether you want to encrypt your /home folder, and I've obviously said yes.

Do you have any idea whether that can still be decrypted/accessed from within another operating system as well, because I'm kind of stuffed without it I'm afraid.

Once again ... thanks for all of your help so far.

Much appreciated,

--David

---

