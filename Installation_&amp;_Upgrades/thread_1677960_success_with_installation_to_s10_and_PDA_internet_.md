---
title: "success with installation to s10 and PDA internet sharing problem"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by nighttrap on 2011-01-29
I am a chronic windowser, and I have just began to use ubuntu. The reason is that windows 7 is running very slow in my new netbook. At first I tried ubuntu netbook remix, but I had too many problems with that, so I decided to install the complete form, meaning ubuntu dekstop edition. I wanted to share my experiences

Installation;
1) I prepared a bootable usb and booted with it
2) At boot menu, I choose "install ubuntu" and pressed "tab" to edit options
3) I deleted "splash" and wrote "intel_idle.max_cstate=0" and pressed enter
4) Installation went fine
5) After restart, computer did not boot of course
6) I pushed the shutdown button of computer
7) Then I restarted again, and after bios screen, I immediately pressed Tab button
8) At the aftercoming screen, I selected "e" to edit options, and wrote again "intel_idle.max_cstate=0" between "ro" and "splash" 
9) I rebooted with ctrl-x to boot
10) Finally, ubuntu desktop edition booted
11) Then I went to "Terminal" and wrote "sudo nano /etc/default/grub" and wrote my pass
12) At that screen I found "splash" and wrote "intel_idle.max_cstate=0" AFTER splash
13 I pressed ctrl-X, pressed Y(es) and enter
14) After that I wrote "sudo update-grub"
15) That's all, you can reboot without any problem

Installation HL-2040 through network
I have a printer connected to my modem via usb slot. I searched many websites, but I could not get an answer to make it work. At the end, I found a solution (it was so hard for me, I am a newbie :()

1) I installed brother HL-2040 drivers from synaptic package manager
2) System - Administration - Printing
3) Add - Network Printer - Appsocket/HP Jetdirect
4) URl was (machine name) 192.168.2.1 in my case and port number was 9100 (see your modem for specific ports)
5) Selected my printer in the next page
6) Ubuntu searchs for drivers (which I installed it at the beginning)
7) That is all :guitar:

I also installed Mac OS appearance, it is very nice, especially for ex-windowsers like me

Now my problem
I have two PDAs. With activesync or windows mobile device center, I could bind to computer and update my spb weather data and GPS positions. I can pair my PDAs with ubuntu, but I dont know how to update these datas in my PDAs, using internet sharing. Updating via GPRS is expensive, and not always I can find wireless. Furthermore, my samsung cannot connect to the modem. Is there any way to update my PDAs data through ubuntu?

Thank you very much

P.S. Sorry for the English, I am not a native speaker:confused:

---

