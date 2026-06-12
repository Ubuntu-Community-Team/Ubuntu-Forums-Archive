---
title: "Size of swap directory"
date: 2020-06-14
forum: Installation &amp; Upgrades
---

### Post by Ranbunta_Bantubunt on 2020-06-14
Hi, I'm about to do an install of ubuntu onto a laptop with 64gb ram. I am using the (almost)-full disk encryption method specified here:

[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

Regarding size of the swap space, the guide indicates:

> I am also creating a 4GiB LV device for **swap** which, as well as being used to provide additional memory pages when free RAM space is low, is used to store a **hibernation**  image of memory so the system can be completely powered off and can  resume all applications where they left off. The size of the swap space  to support hibernation should be equal to the amount of RAM the PC has  now or is is expected to have in the future. 


For this device (which will have a 2TB M.2 flash drive for storage, so swap can be big), I am wondering how large to make the swap space. I would like to use the hibernation feature. 

Since the machine will have 64gb, according to the guide swap should be 64gb. However, what if the swap space is already being used for something else? I plan to run several VMs simultaneously which is why the machine needs 64gb ram. Maybe swap should actually be 70 gb, in case 6 gb of swap are being used for other things, plus I hibernate? 

Also I would hesitate to make the swap space exactly 64GB as these days, there could be differences in how a "GB" is calculated that I fear might lead to it being slightly smaller than the actual amount of ram, even if both "Swap" and "RAM" are nominally 64 in the category of "GB", or maybe some overhead is needed on top of the actual memory in RAM, who knows, seems like it would be prudent to pad it just a little bit to be sure.

Any tips?

Thanks

---

### Post by T6&amp;sfpER35% on 2020-06-14
> [COLOR=#000000] laptop with 64gb ram[/COLOR] 
:shock:

from what iv'e gathered reading through numerous posts,is that it is advisable not to create a swap partition manually.
just do the install and let it create the swap automatically.

EDIT:scratch that , only see now you mention "[COLOR=#000000]I would like to use the hibernation feature." and "[/COLOR][COLOR=#000000]I plan to run several VMs simultaneously"

note to self...read posts properly before jumping on..[/COLOR][-X

---

### Post by GhX6GZMB on 2020-06-14
Your swap partition should be a bit larger than your RAM.
But ask yourself if you really need this feature. If you need to preserve the machine state indefinitely, go ahead. But be aware that a resume from hibernate takes longer than a cold boot.

---

### Post by TheFu on 2020-06-14
Don't use hibernation if you use whole drive encryption.  it drastically reduces the security.

i use standby for days with my laptop, but never when it gets moved.  During movement, the system is completely off, for security reasons.  Data encrypted at rest.  i figured I&#8217;d not be able to predict a car accident or a random theft walking between buildings on a college campus.

---

### Post by Ranbunta_Bantubunt on 2020-06-14
> **TheFu said:**
> Don't use hibernation if you use whole drive encryption.  it drastically reduces the security.

i use standby for days with my laptop, but never when it gets moved.  During movement, the system is completely off, for security reasons.  Data encrypted at rest.  i figured I’d not be able to predict a car accident or a random theft walking between buildings on a college campus.

I don't really need hibernation, I just have historically used it in the past. Not a big deal to give it up. 

But, if the swap area is encrypted, how does hibernation reduce system security? When you say it reduces security, are you assuming the swap area is unencrypted?

---

### Post by grahammechanical on 2020-06-14
The evidence is hard to find but I remember talk of Ubuntu switching to swap files instead of swap partitions for new installations of Ubuntu. An already existing installation that is using a swap partition when upgrade to the latest Ubuntu will continue using a swap partition.

My install of 18.04 upgraded from 16.04 has this;

> graham@sdb1-sdb8:~$ sudo swapon --show
[sudo] password for graham: 
NAME      TYPE      SIZE  USED PRIO
/dev/sdb5 partition   2G 23.3M   -2

The swap partition size of 2GB is twice the RAM that I had in this machine when I first installed this Ubuntu. I now have 4 GB RAM.

I will edit this post in a few minutes after I have run that command on a 20.10 install upgraded from 20.04

Edit: @CatKiller. Thanks.

My 3 Ubuntu installs are all using the swap partition.

Regards.

---

### Post by CatKiller on 2020-06-14
> **grahammechanical said:**
> The evidence is hard to find but I remember talk of Ubuntu switching to swap files instead of swap partitions for new installations of Ubuntu. 

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes) 

> **Other base system changes since 16.04 LTS**

For new installs, a swap file will be used by default instead of a swap partition. 

---

### Post by Ranbunta_Bantubunt on 2020-06-14
Here's some screenshots and an excerpt from the install guide I linked to, which I will be following with my new install coming up. In this setup, two encrypted partitions containing encrypted volume groups are created. One contains /boot. The other contains the swap area, and the root file system.

So the swap area is encrypted in this setup.

/dev/mapper/ is the path to encrypted volumes that are created within 

code creating the encrypted root and swap area:

```
# pvcreate /dev/mapper/${DM}5_crypt
  Physical volume "/dev/mapper/sda5_crypt" successfully created.
# vgcreate ubuntu-vg /dev/mapper/${DM}5_crypt
  Volume group "ubuntu-vg" successfully created
# lvcreate -L 4G -n swap_1 ubuntu-vg
  Logical volume "swap_1" created.
# lvcreate -l 80%FREE -n root ubuntu-vg
  Logical volume "root" created.
```

[IMG]https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019?action=AttachFile&do=get&target=012-Install-Installation-Type-03.png[/IMG]

[IMG]https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019?action=AttachFile&do=get&target=015-Install-Installation-Type-06.png[/IMG]

---

