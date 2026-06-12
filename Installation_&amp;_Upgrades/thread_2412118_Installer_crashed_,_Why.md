---
title: "Installer crashed , Why ?"
date: 2019-02-08
forum: Installation &amp; Upgrades
---

### Post by maks88 on 2019-02-08
Using Rufus to create bootable image on mine windows 10  (The OS came with the laptop from the store) .  Laptop model Lenovo Y720 .. 
  
[LIST=1]
[*]I tried to create MBR/GPT partition schema with ISO mode (recomended) . 
[*]I tried to create MBR/GPT partition schema with DD mode 
[/LIST]
       3.The modes i tried to load mine usb and maybe overcome this problem , UEFI and Legacy . 
  The OS Ubuntu is up and running in all 3 cases .. 
  But when it come to partitions here it begins . 
  No root file system , well Ok i am trying to make one but , it won't  let me for example . If i choose the 512 000MB partition creation it  create for me only 1MB partition and 0MB partition .  The problem is that i can't create any partition with volume i need and  set it to root .. I tried anything + ext4 filesystem format . 
  Does anybody had this kind of problem ?   
  I got last Ubuntu version LTS downloaded today from their site . 
  The strange thing is that , on mine second laptop i tried to install  Kali Linux and it required from me the DD mode for the OS image in order  to work , but for this case i have no idea what i need to do .. 
  Mine home PC has Ubuntu installed exactly the same version and working good.
  After trying to install another OS BackBox , i got the stack error  when i moving during installation to the Installation type stage, when i click on change or '+' buttons in the menu to add or change  partitions as above
i got this errors: For Ubuntu problem i don't have any stack trace .. 

[CODE]Installer crashed :     
Traceback (most recent call last):     
File "/usr/lib/ubiquity/plugins/ubi-partman.py",line 1293 in  on_partition_list_new active self_.partman_dialog(devpart,partition)     
File "usr/lib/ubiquity/ubiquity/plugin.py",line 48,in wrapper ,  return target (self,*args,**kwargs,)     
File "usr/lib/ubiquity/plugins/ubi-partman.py",line 956, in  partman_dialog     Type_Error:'NoneType' object is not subscriptable[/COD

---

### Post by yancek on 2019-02-08
You have windows 10, do you want to keep it?  If so, use windows Disk Management to shrink the windows partition to create unallocated space on which to install Ubuntu.  Windows 10 pre-installed on a GPT partitioned drive needs to be UEFI and if you want to boot both windows/Ubuntu from the menu, you need to also install Ubuntu UEFI.  Instructions/information on this is at the Ubuntu site at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by maks88 on 2019-02-08
No i don't need windows , i need only Ubuntu installation ..

---

