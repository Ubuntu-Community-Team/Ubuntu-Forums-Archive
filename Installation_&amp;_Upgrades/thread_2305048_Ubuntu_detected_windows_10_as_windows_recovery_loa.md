---
title: "Ubuntu detected windows 10 as windows recovery loader"
date: 2015-12-02
forum: Installation &amp; Upgrades
---

### Post by khaled10 on 2015-12-02
hello ubuntu users 

I install ubuntu in dual boot whit windows 10 but it give me error winloader.exe cant run from  when i enter whit windows 8 loader  i can enter just whit windows recovery environment in sda 2 how i can change sda 2 to sda 1 ? 

I ready check some command line in ubuntu for repair boot and grub menu it give me that 

[http://paste.ubuntu.com/13605096/](http://paste.ubuntu.com/13605096/)

im waiting some help thank you ubuntu users.

---

### Post by yancek on 2015-12-02
Your boot repair output shows sda2 marked as active/bootable which is necessary with a windows system.  This is your Recovery partition so changing to make sda1 as active using GParted should help.  GParted is on the install medium.  See the link below.  Not sure this will work as you don't seem to have the boot files showing on sda1 that you have on sda2.  If this doesn't work, you can always change it back until someone more familiar with using windows posts.

 [http://thpc.info/how/make_active.html#gpart](http://thpc.info/how/make_active.html#gpart)

---

### Post by khaled10 on 2015-12-02
thank you for your reply yaneck , yes sda 2 it showing as active bootable because winloader in sda2 [COLOR=#000000]/bootmgr /Boot/BCD /Windows/System32[/COLOR][COLOR=#000000]oad.exe ! and not in sda1 , when i install ubuntu i give it 20 gigabytes 2 go for swap partition logical partition and rest / boot , uefi support , i try some commande for windows [/COLOR][COLOR=#191919][FONT=monospace]bootrec /rebuildbc 
[/FONT][/COLOR][COLOR=#000000]howerver still dont work im not sure Gparted will give sda 1 boot system , now im working in recovery windows sda2 until find solution for that . [/COLOR]

---

### Post by oldfred on 2015-12-02
If you had boot flag on sda2 when you installed Windows 10, then you only installed the new boot files in sda2 and have old version boot files in sda1.

Windows normally installs to two partitions a small (hidden) Boot partition and large main install (c:) drive. But will install to one partition if NTFS main partition created in advance and has boot flag. That was so Windows 7 could install into Vista as Vista installs never had separate Boot partition.

---

### Post by khaled10 on 2015-12-02
hello yanick  i find something whit gparted sda 1 it for partition system of windows ! it read like os windows 10 and sda 2 recovery windows but in real it windows 10 not recovery do you inderstand me

---

### Post by khaled10 on 2015-12-02
Hello oldfred thank for join us 

I inderstand what do you mean  but in my situtation it different because sda 1 it just partition system of windows 10 not windows 10 partition and sda 2 like you see in picture where windows 10 installed , it not recovery system , i think that i forget to hidden partition system sda 1 because ubuntu detected it like os windows 10 !

---

### Post by oldfred on 2015-12-02
Depending on version of Ubuntu grub2's os-prober, it has not been updated to find Windows 10. 
It progresses thru all the versions and if still Windows but unknown version it labels it Recovery. 
You can manually update description by turning off os-prober and copy boot stanza into 40_custom. Then entry in 40_custom you can edit description at will.

You also show that Boot-Repair cannot mount sda2. That normally is that you left Windows hibernation on or what it now calls fast start up. You must turn that off if dual booting.
       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html

      [/URL]
 One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.
[http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910](http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910)

   Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

    
When new boot stanza is proven to work, you eliminate the os-prober versions Add the line to grub configuration file:
 gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by khaled10 on 2015-12-02
thank you oldfred i inderstand what do you means however way 2 im not sure will success i need know how it work for dont loss my os win 10 anyway i still working whit sda 2 recovery and speed up startup because it low in startup

---

