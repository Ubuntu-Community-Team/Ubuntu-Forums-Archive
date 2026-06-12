---
title: "Problem installing 6.06 Server"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by rsain on 2007-05-31
I need to install 6.06 server on a sunfire x2200.

It currently has 7.04 server running on it. 
When I try to "install to hard disk" from install CD the system hangs and displays the following

```

Decompressing Linux...done.
Booting the kernel

```

It doesn't get past this. 

[LIST]
[*]I tried using the "rescue mode" - same issue.
[*]I tried using the 'alternate cd' and got the same issue.
[*]I tried using Edgy and got the same issue.
[*]At one point I figured I'd get some sort of message if I just waited. I waited for 48 hours. No message other than the above.
[*]As soon as I put in the 7.04, bingo. No problems. But I need to be able to run Dapper Drake. 
[/LIST]

I've all but destroyed my few remaining follicles - any help would be greatly appreciated.

- Ryan

---

### Post by rsain on 2007-05-31
And yes, as far as I can tell I have thoroughly searched the sticky post. This is not an upgrade situation, it is a downgrade or clean install problem (see below). Nor is it a situation of being setup as a virtual system (it's its own box).

------
*Update
-----

I just tried putting in a clean drive (opened from package) and starting from scratch. Exact same problem! Odd!

We recently installed 6.06 Server on two Sunfire x4100s with no problems (SAS drives) with no problems. Is this possibly a hardware issue?

-Ryan

---

### Post by louieb on 2007-05-31
Time to play with cheat codes. Knoppix is Debian based so most of these are valid to.
 [BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

---

### Post by rsain on 2007-06-05
I'll give them a shot...

Thanks.

- Ryan

---

### Post by rsain on 2007-06-05
Update:

Tried the following:
1.  noapic nolapic 
2. noacpi
3. noacpi noapic nolapic
4. gdth=disable
5. sym53c8xxx=safe

all to no avail.

I also tried the vga=771 but that just made things worse (didn't display anything).

Here are my boot options as they exist when I try to install from CD:

```

Boot Options preseed/file=/cdrom/preseed/ubuntu-server.seed/ initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --

```

Shouldn't the kernel be defined? Is it possible that it's looking in the wrong spot? (remember I already have this box running as 7.04 and I'm trying to downgrade)

I remember when installing 7.04 that things were a bit different (seems like the root is amis - but not sure IIRC what the old one was - compare to this though, which looks much closer to my Feisty install - [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) ) and the RW option was previously set as RO. 



Help!!! :D

- ryan

---

### Post by rsain on 2007-06-06
update:

in a fit of frustration I decided to try the Desktop version..... well, same problems. 

I"ll keep testing boot options.

- Ryan

---

### Post by rsain on 2007-06-06
Just in case more information helps folks - I ran the install with the quiet option removed. The last 4 lines are as follows:

```

[ 1015.843894] io scheduler noop registered
[ 1015.844006] io scheduler anticipatory registered
[ 1015.844119] io scheduler deadline registered
[ 1015.845232] io scheduler cfq registered

```

At this point it just hangs.

- Ryan

---

### Post by rsain on 2007-06-10
Thanks for the long term support! 

I gave up and went to Debian. Worked like a charm. 

Truly - thanks to those that replied about this issue. 

So - conclusion: Don't try installing 6.06 or 6.10 on a Sun Microsystems Sunfire X2200. So far as I can tell it won't work. 

- Ryan

---

