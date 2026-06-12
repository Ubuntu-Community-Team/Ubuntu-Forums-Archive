---
title: "Can't get past Grub"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by Tholley on 2011-07-12
Recently I did a clean install of Windows 7 on my HP Desktop because of registry issues, and wanting to clear the XP partition I was no longer using.
 
I also had Ubuntu 10.04 as a 3rd partition which worked fine. 
 
After the clean install of Win7, it is working perfect, I decided to put 11.04 as a second partition. I gave it 200gb of the 750gb HDD. It said it installed, but after Grub, it would just show a jumbled screen and freeze. So I figured maybe a video card issue, so I tried to install 10.10, when I would select it in Grub, my monitor would go to sleep as if it is no longer receiving a signal.
 
So I go back to 10.04 since it worked on the same machine before. I did everything as before, did it manually by setting EXT4, checking to format the partition, and mount point = /.
 
It seemed to install just fine, but now when I select Ubuntu in Grub, it just goes to a black screen with the cursor blinking in the top left corner. I left it like that for a while too, just to see if it would eventually get there, but never did. Tried a couple more times and still the same.
 
I can choose Windows, and it will boot into W7 just fine.
 
It is an HP Pavilion Media Center, with 750gb HDD, 4GB DDR2 ram, AMD Athlon 64 CPU, GeForce 6150 LE chipset.
 
Could it be the EXT4? Should I retry and select EXT3 instead?
 
Like I said before, 10.04 worked fine before, so I can't understand why it wont now.
:(
 
Thanks, Terry

---

### Post by perspectoff on 2011-07-12
See if these are apropos:

[http://ubuntuforums.org/showthread.php?p=10747748](http://ubuntuforums.org/showthread.php?p=10747748)

or

[http://www.kubuntuguide.info/index.php/Template:Natty/Hardware#Frequency_Out_of_Range_.2F_Choose_New_Resolution](http://www.kubuntuguide.info/index.php/Template:Natty/Hardware#Frequency_Out_of_Range_.2F_Choose_New_Resolution)

---

### Post by Tholley on 2011-07-12
I'm not getting any "frequency out of range" messages, but I definitely will give it a try later when I get back home. I suppose it will still work if I do it from the LiveCD?

---

### Post by Quackers on 2011-07-12
Try a boot option like nomodeset for instance. It sounds like a video problem.
What graphics card are you running?
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Tholley on 2011-07-12
I have always had to x - nomodest when booting 10.04 livecd. (if that is what you are refering to)
 
and it is just an integrated graphics card on the Asus MBoard. Nothing has changed on the computer since it was working w/o any problems before, other than re-installing the OS's.

---

### Post by Quackers on 2011-07-12
No, but the kernel has.

---

### Post by Tholley on 2011-07-12
> **Quackers said:**
> No, but the kernel has.
 
Even tho I used the same 10.04 cd as before (when all was working fine)?

---

### Post by Quackers on 2011-07-12
Ah ok. So you used nomodeset boot option when you had 10.04 installed earlier. Or was that a modeset= option? And was that required to boot the installed system too?
Obviously if you are using the same option now it should work. Maybe it isn't a video problem.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Tholley on 2011-07-12
I was looking thru my old threads from when I installed 10.04 last time, and it seemed I had the same kind of issue, (I tend to forget all that once I get it all up and running:-\")
 
I am going to try this first when I get home...
 
```
[SIZE=4]
[SIZE=1]You'll most likely just have to add "nomodeset" through grub during your first boot. At the grub menu, highlight your Lucid kernel and hit 'e'. Then type "nomodeset" after "quiet splash". Ctrl+x to boot.

Then make sure your nVidia drivers get installed through System->Administration->Hardware Drivers.[/SIZE]
[/SIZE][SIZE=2][/SIZE]
```
 
I guess since I had to x the nomodeset on the live cd, I need to do it on regular boot as well?
 
If that doesn't do it, then I'll post the info you asked.

---

### Post by Quackers on 2011-07-12
If the live cd needs a boot option the installed system will need the option too, at least for the first boot ( and with an integrated video card, maybe ever after).
Good luck :-)

---

### Post by Tholley on 2011-07-12
Thanks!

---

### Post by Tholley on 2011-07-12
All is good now!
All I had to do was type the nomodeset after quiet splash, and that got me in, and then once I updated the nVidia driver, it all worked like before!

One of these days I'll remember these things...   ](*,)

thanks for all the help and I hope this helps somebody else in the future as well!

---

### Post by Quackers on 2011-07-13
Ok that's good to hear :-)
Enjoy!

---

