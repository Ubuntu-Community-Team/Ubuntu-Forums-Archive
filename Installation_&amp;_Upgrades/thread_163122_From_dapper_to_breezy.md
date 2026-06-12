---
title: "From dapper to breezy"
date: 2006-04-20
forum: Installation &amp; Upgrades
---

### Post by jen140 on 2006-04-20
Hi ppl ,need a little help with thise... just formated a pc , and installed dapper flight ,but now i see ,that ,many programms doesnt work .... my friends said me that the best way is to put a stable version on thise pc....so i have chosen the breeze ,so is there any way to update it  ,without losing information from the hard drive ?

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=jen140]Hi ppl ,need a little help with thise... just formated a pc , and installed dapper flight ,but now i see ,that ,many programms doesnt work .... my friends said me that the best way is to put a stable version on thise pc....so i have chosen the breeze ,so is there any way to update it  ,without losing information from the hard drive ?[/QUOTE]
no..

next time, you might want to have a separate partition for /home so you won't have to format everything when you need to install a distro.. 

[www.tldp.org/HOWTO/Partition/](www.tldp.org/HOWTO/Partition/)

---

### Post by kwaanens on 2006-04-20
But you can make a backup by burning
/home (except .gnome* directories which might generate problems with regards to the look and feel of you desktop)
/opt (if anything's there)
/var (if you need it)
to a CD and then copy the stuff over from the CD to the fresh install of Breezy.

I usually also copy /etc/fstab, /etc/samba/smb.conf (for Samba) and /etc/hosts (for NFS) to a CD as well, to be used as references when you set up your new system again.

However, Dapper is pretty stable by now, just disable Assistive technology ($ gnome-at-properties).

Which applications doesn't work for you?

- Ketil

---

### Post by jen140 on 2006-04-20
Just wanted the "automatix " working ,and "vmware" too ....
installing vmware , get "What is the location of the directory of C header files that match your runningkernel?" and dont know where it is :( and automatix ,is for breezy ,ty for help anyway.

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=jen140]Just wanted the "automatix " working ,and "vmware" too ....
installing vmware , get "What is the location of the directory of C header files that match your runningkernel?" and dont know where it is :( and automatix ,is for breezy ,ty for help anyway.[/QUOTE]
automatix should just work in a breezy install. I don't know of a dapper port yet. 

as for vmware, make sure you ```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential linux-headers

``` in breezy

if these are done, you'll just accept defaults given in vmware installation prompts (that's how I did in my vmware installation). 

above should work with dapper as well.

---

### Post by jen140 on 2006-04-20
"/tmp/vmware-config0/vmnet-only/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined"
always gives thise error ,what can i do ?
> However, Dapper is pretty stable by now, just disable Assistive technology ($ gnome-at-properties). when i installed ,itwas already disabled...

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=jen140]"/tmp/vmware-config0/vmnet-only/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined"
[/QUOTE]
can this be due to gcc? try this:
1. run the uninstallation script, if any:
type vm in terminal, and double tab (tab key in keyboard). it will show you all commands starting with vm. run the correct command with sudo vm..... sorry I just don't remember the name of the command

2. install gcc: 
sudo apt-get install gcc-3.4

3. try installing vmware again:
CC=gcc-3.4 sudo vm.......

vm........ is the installation script this time. I don't remember its name either...

hopefully someone will fill in my blanks :)

---

