---
title: "Install is stuck. Is it safe to reboot?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Tom Chaudoir on 2007-04-20
Overview:
I used the update manager per instructions. With an estimated 40 left to go, the upgrade stopped. Now I'm afraid to kill it or reboot. Advice please!

Details:
All the files were downloaded and the upgrade well under way. I left for a couple of hours. When I got back the terminal was in sleep mode and woke up when I moved the mouse. A dialog window was on top of the upgrade window. It said something about file differences but the box was blank. No differences? I selected what looked like the default. I believe it was something like "keep old file". Or not. Sorry. I didn't know it might be important.

The dialog went away. The terminal window in the upgrade manager looked like it was waiting for an answer. I couldn't type anything or copy what was in the window. I came here meaning to type in what the text in the term was. Now the window is empty gray space so that can't happen either.

From memory: It said something about an init file that had been deleted by me or a package. The new package had a replacement. It gave me like 5 one letter choices. The default was "N" so that's what I tried but it wasn't responsive.

Even more details:
I just opened the terminal and it looked different. A yellow background. I'm assuming it's a feisty thing. Running top produced:
 top - 10:33:56 up 20:56,  1 user,  load average: 1.52, 0.74, 0.46
Tasks:  70 total,   1 running,  68 sleeping,   0 stopped,   1 zombie
Cpu(s):  7.3%us,  1.3%sy,  0.0%ni, 91.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    248028k total,   244464k used,     3564k free,     4740k buffers
Swap:   722884k total,   307492k used,   415392k free,    63244k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3915 root      15   0 35008 7596 3424 S  5.3  3.1  22:32.10 Xorg               
 4326 tom       15   0  135m  68m 8076 S  2.0 28.3  18:30.07 gnome-panel        
 4232 tom       15   0 22188 3032 2148 S  1.0  1.2   9:07.85 at-spi-registry    
21947 tom       15   0 58708  17m  10m S  0.7  7.3   0:01.18 gnome-terminal     
 4320 tom       15   0 17548 6036 4972 S  0.3  2.4   2:13.00 metacity           
21903 tom       15   0  166m  61m  20m S  0.3 25.3   2:28.97 firefox-bin        
21970 tom       16   0  2312 1136  880 R  0.3  0.5   0:00.11 top                
    1 root      16   0  1712  412  412 S  0.0  0.2   0:02.17 init               
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0  

That's about all I can think to provide. I'm a Linux noob. How do I bail this thing out? Thanks.

Tom

---

### Post by az on 2007-04-20
From a terminal run

sudo apt-get -f install

and that should do it for you.

---

### Post by Tom Chaudoir on 2007-04-20
I tried it. No joy. It said that another program was using something that it needed. I xkilled the frozen update manager and tried again. Same thing. So maybe some other program is using it. I rebooted.

Bad move. It won't boot, even in recovery mode (Whatever that is). I'm really stuck.

To post this I booted a live 6.10 CD. Can I use that to somehow repair my installation? I really don't want to wipe the drive and start over. Any suggestions welcome.

Best,
Tom

---

### Post by DarkStarAeon on 2007-04-20
When the upgrade hangs, just let it sit for however long it takes to pop up an error message dialog, then click the ok button and it will abort on it's own. Then go to System > Administration > Update Manager and start the process over again, it will look like it's starting from scratch, but eventually it goes back to picking up where it left off.

What to do in your current situation? I don't know. sorry.

---

### Post by az on 2007-04-20
You can mount your installation in the live cd and then chroot into it.

sudo chroot /media/sda1

and then from there,

sudo apt-get -f install

---

### Post by Tom Chaudoir on 2007-04-21
Thanks az. That did the trick. I'm back to good old 6.10. Actually it took a good deal more than that. I'll show my work in case another noob runs into this.

My ubuntu drive is hdb1. For most people I think it will be hda1. Change as needed.

Boot the live 6.10 CD. Open a terminal. Now make a mount point for the hard drive:
sudo mkdir /media/drive

Make it read/writable:
sudo chmod 777 /media/drive

Now mount the drive:
sudo mount /dev/hdb1 /media/drive

Change chroot to the mounted drive:
sudo chroot /media/drive

Now fix the installation:
sudo apt-get -f install

At this point it complained about dpkg and told me to run:
sudo dpkg --configure -a

I did that and it took hours. It stopped many times and asked what to do about changes in different files. In every case I typed an upper case "N". Worked for me. There were a lot of scary errors and messages. Guess they didn't matter because I seem to be 100% OK.

After the dpkg I ran the apt-get and then rebooted. I'm a happy camper. Thanks again.

Best,
Tom

Late edit: Things were looking slightly different. Guess what. It didn't revert to Edgy. I have a working upgrade to Feisty. Cool.

---

