---
title: "grub problem, i think..."
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by jklopez on 2011-06-25
i start my laptop and get what os option win7 or ubuntu 10.04 i put win7 and all is well but if i pick ubuntu a screen that says:  starting cmain... ,a second later a screen appears that says ... Grub4DOS 0.4.5b 2011-04-23,mem:638/1406/0m,end 351489
           [minimal Bash-like line editing is supported.For the first word,TAB list possible         command completions.Anywhere else TAB list the possible completion of a device/filename.] .....under that it says grub with the flashing cursor like if it was waiting for me to type something,  i dont know too much about linux,  i can tell you that i'm installing on a 1tb external hdd (through yumi usb)and the install went fine ,at the end ,it said that i need to reboot before i can use ubuntu , but after reboot no ubuntu , just win 7 so through win7 i used easyBCD and followed ...[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)  .....and now i reboot and i see win7 and ubuntu but when i pick ubuntu i get the problem described above ....my laptop is a toshiba satillite a75 and has 1.50gb ram /dual 3.20ghz prossesors ...any help would be great....p.s. if this is hard to read .....sorry i left extra dots and spaces so the letters don't seem so jumbled together..

---

### Post by YesWeCan on 2011-06-25
So you have installed Ubuntu on an external USB drive? When you did the installation did you explicitly tell the installer to put the boot-loader on the USB drive? If you did, you should be able to boot the USB drive from the bios, bypassing Windows entirely. Does the USB drive boot?

---

### Post by jklopez on 2011-06-25
At the last step of the install ,under advanced i put the bootloader on the external drive ,on the partition that ubuntu has installed to...i read a couple of minutes ago the theres a bug that prevents(10.04 ONLY) you from installing boot loader to an external drive even though you mark it and the install go's fine ,so i used easybcd again to install it's pwn grub and now after i reboot and  choose ubuntu(neo-linux is acually what it says) i no longer get that error now i get .....booting/grub/grub.conf
     find --set-root--ignore-floppies/grub/grub.conf
     error:15 :file not found
     press any key to continue.....i press space bar and i get what looks kinda like windows boot manager ,i assume it's the neogrub2 boot manager and my options are...
     /boot/grub/menu.lst
     /grub/menu.lst
     /boot/grub.conf
     /grub/grub.conf
                  any ideas ...oh yah....no i cant bypass windows and boot ubuntu directly through the bios..

---

### Post by YesWeCan on 2011-06-25
Ok. So there are a few tasks needed.
1) Get Grub on the MBR of the external disk. This is so you have the option to boot it directly and so you can reliably chain load it from the Windows boot-loader. The arrangement where Grub is in a partition like that is not reliable.
2) Restore your internal HD MBR so you can boot Windows
3) The Grub on your external may be legacy not Grub2. Ideally, this should be upgraded.

To be sure about what's what would you download and run this and post RESULTS.txt in code tags?
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

