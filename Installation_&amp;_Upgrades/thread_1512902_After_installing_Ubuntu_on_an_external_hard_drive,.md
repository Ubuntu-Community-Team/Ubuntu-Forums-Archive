---
title: "After installing Ubuntu on an external hard drive, Windows Vista won't boot"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by SiruDrawoh on 2010-06-18
Hello, I wish my first post were on happier circumstances. I've been  trying and searching for hours for a fix, but I've had no luck. First  things first, I received my copy of Ubuntu 10.04 in the mail yesterday  and, after extensive modifications to my Windows XP computer (added a  new CD drive since my old DVD/CD drive died as well as the installation  of a floppy drive and two more USB ports. Made sure Windows booted up  normally before attempting the install, as it was the computer I  requested the Ubuntu CD for) I popped in the CD, restarted, and started  the installation as instructed. At about 53%, it gave an error stating  the files could not be completely copied which was usually caused  because of a bad CD drive, stopped, and shut down. I booted it up,  watched as the BIOS loaded and attempted to boot the system and...  nothing. My computer was stuck at a black screen with a blinking _.  After leaving it there for about an hour, I decided that I had ruined  the computer. So after that bit of fun, I got another idea. I had a  perfectly good computer and a perfectly good external hard drive, so why  don't I use the other computer (which is the main computer in the  house) to install Ubuntu on the external hard drive, then boot my other,  now wonderfully dead computer from the external hard drive? Well, I  decided to go ahead and do it, even though there was a disturbing  thought in my head that constantly said "Knowing your luck, this is  gonna go horribly wrong..." And now, after it completely installed on  the hard drive (I checked it seven times to confirm that it was  installing on the right drive) my other computer won't boot through the  external hard drive (sign one that I should have listened to by  paranoia) and my Windows Vista Home Premium computer, the computer that  had all my important programs on it (such as my home recording studio...:mad:)  will not boot. When I turn it on, it gives me a message stating: error:  no such device: fef3ed3c-fe88-4d5a-8f95-d1988c2df7cc. Then has what I  assume is a command line prompt or something since I'm able to type  things after the grub rescue> thing. So after all that, I got chewed  out and yelled at by my family, and as you can imagine, I now feel like  the biggest prick on earth. Now to what I did earlier this morning. I  came downstairs around 3 a.m. central time and took my very old, fried  computer and harvested the hard drive from it (this is the same computer  I took the CD drive, the floppy disc drive, and the extra USB ports  from) and replaced it with the now unresponsive drive in my XP computer,  so that temporarily solved one problem. I then downloaded a Windows  Vista 32 bit Recovery Disc from  [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/). I  booted from the disc on my Vista computer and ran the system repair  tool. The first time it seemed like it was fixing whatever was wrong  with it, and after over an hour, it said to restart the computer. I did  and... it still didn't boot...:mad:  Gave me the same no such device error. I tried the repair again and it  said there was nothing to repair (not the exact words, but that's what  it meant). So now I've decided to get some outside help. Here's the  system specifics that I can remember:

Windows Vista Home Premium  32 bit
The brand is E-Machine
Running an Intel Celeron Dual-Core  processor
Has some NVIDIA graphics card in it
Cost around 500$ (A  little less with our Wal-Mart discount card)
Before this it worked  perfectly

Let me know if you need anymore information about the  system (I know I don't have a lot of info on it but I don't use it THAT  much). Any help you can give me is greatly appreciated and thank you for  your time.

---

### Post by darkod on 2010-06-18
Disconnect the usb hdd from your vista machine you want to repair, boot with the ubuntu cd in live mode, Try Ubuntu option.

Open terminal (in Applications-Accessories) and execute:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

After the first command it will give some warnings that will sound scary. Ignore them, it's normal. Just run the second command when the command line appears.

Restart without the cd and vista should boot. Provided you didn't do more damage trying to fix it. :)

We'll talk how to sort out your usb hdd after you get vista up and running. You should still have ubuntu installed on it that you can use.

---

### Post by SiruDrawoh on 2010-06-18
HDD is removed, booted from the Live CD.
Opened the terminal and entered the first command. After a few messages it presented a yes or no option. I ignored it since you did not say anything about that and instead of typing yes or no I inserted the second command. It responded with the word "Abort".
Exited the terminal, restarted computer without the disc and received the same no such device error.

Am I doing anything wrong?

---

### Post by darkod on 2010-06-18
The first question is yes or no whether you want to install, you need yes there. When it starts installing it, there will be WARNING messages, ignore them. The second command failed because the first didn't install lilo. Redo them.

---

### Post by SiruDrawoh on 2010-06-18
Okay, I selected yes then after a bunch of Err and Failed messages, it gave me the command line. Entered the second command and it now gives me the message sudo: lilo: command not found.

---

### Post by darkod on 2010-06-18
Hmm, there should not be err and failed messages. I guess it didn't install. Hence it couldn't find the command for the second command.

Do you have internet access while trying this? You will need internet to install them.

Alternatively, try again with the neosmart vista cd and the manual instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by SiruDrawoh on 2010-06-18
My ethernet cable was unplugged! O.o Trying it again.

Alright! It worked perfectly! Thank you so much for your great instructions. I never knew that it would take two simple commands. Again, thank you very much!

---

### Post by darkod on 2010-06-18
> **SiruDrawoh said:**
> My ethernet cable was unplugged! O.o Trying it again.

Alright! It worked perfectly! Thank you so much for your great instructions. I never knew that it would take two simple commands. Again, thank you very much!

Well, that's the linux way. Even where vista own repair process fails, it can help you repair windows boot. :)

---

### Post by SiruDrawoh on 2010-06-18
That's pretty awesome. So now I don't have to fear the wrath of my family and me and Kyle can continue recording our music. It's a win for everyone. So why exactly did installing Ubuntu to an external hard drive mess up the computer?

---

### Post by darkod on 2010-06-18
Common slip up when installing to ext hdd. In the last screen of the installer before clicking Install, you should have clicked on the Advanced button. That will allow you to select where grub2 to be installed. If you want to boot the computer also without the ext hdd, you need to put grub2 on the ext hdd.
Instead it went onto the int hdd mbr, and since that is only part of grub2 that continues to load its configuration files from the ubuntu partition, when the ext hdd is not there grub2 on the int hdd mbr just gives an error. No config files to load.

If you want to use the ext hdd with ubuntu you need to plug it in now, and boot again the ubuntu cd in live mode, and add grub2 to the mbr of the ext hdd. Otherwise there is nothing to boot it now.

Instructions how to do that are here, make sure you use the instructions for grub2, for 9.10 or beyond:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by SiruDrawoh on 2010-06-18
That makes sense. I suspected something like that happened. Okay, so now that I know how to make my external HDD bootable, is there any way I can recover my old hard drive that is completely unresponsive after the Ubuntu installation stopped at 53% or is it dead?

---

### Post by darkod on 2010-06-18
It shouldn't be dead unless it was real coincidence. Obviously installing any type of OS can't just kill a hdd. :)

You can try booting the ubuntu cd on that computer and try to install again. Especially if you want to install on the whole disk, that's easy with selecting Erase and use whole disk option.

If you suspect the cd or cd drive are bad, you could try bootable ubuntu usb stick. You can even make it from live mode on any computer you can boot with the cd, you just need to also have the image file there.
Or boot your ext hdd ubuntu.
The option to create bootable usb stick is in System-Administration, it's called Startup Disc Creator.
Then try booting from the usb if that computer supports it.

---

### Post by SiruDrawoh on 2010-06-18
Mmkay sweet. Now that that horrific incident of terror is over, I may just be close to actually using my new OS. Thanks for all the help. I learned a lot today.

Update: Got it all installed correctly on my external HDD. Posting this message from my new Ubuntu OS. Thanks again. I can now be excited!

Update 2: Ubuntu would crash at times on the external HDD, so I popped the CD into my Vista computer and made the bootable USB Drive and now my 80 GB HDD that was not responding is running Ubuntu. I like this OS.

---

