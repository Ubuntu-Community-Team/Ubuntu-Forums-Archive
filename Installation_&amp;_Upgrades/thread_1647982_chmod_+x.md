---
title: "chmod +x"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by ThuyT on 2010-12-18
The software I just bought (Lightroom 2.1) contains instructions to get my serial. I downloaded the sofware on my desktop and installed it. In the terminal, I wrote "chmod +x keagan", pressed enter and wrote "./keagan" and I get this message: No such file or directory.

Anybody can tell me what I am doing wrong? I am working on Mac OS 10.4.

I am not super good with computer so I need basic instructions please!! Thanks

---

### Post by gordintoronto on 2010-12-18
For chmod, you need to be in the folder where the file you're trying to affect resides.

To see what files are present, use the command:
ls

When you start the terminal, you are in the Home folder. To get to the desktop:
cd Desktop

---

### Post by ThuyT on 2010-12-18
Thanks. I still get the message "No such file or directory" though. Lightroom, the keagan, and the file "file_id.diz" are all on my desktop, I did write "cd Desktop", "chmod +x keagan" and "./keagan" on the terminal and it does not work. Any idea why?

---

### Post by oldos2er on 2010-12-18
Can you post the output of ```
ls Desktop
``` ?

---

### Post by ThuyT on 2010-12-18
"ls desktop" gives me this result:

Adobe Lightroom 2.app                   
Microsoft Messenger.app
Adobe Photoshop Lightroom 2.1.512205                    
BitTorrent Downloads                    
Documents                             
UnRarX.app
embrace.nfo
file_id.diz
LTRM2_WWEFG_mac.dmg                     
images
keygen

---

### Post by oldos2er on 2010-12-18
So is the file you're looking for 'keygen'? Or is it in one of the folders 'Adobe Lightroom 2.app' or 'Adobe Photoshop Lightroom 2.1.512205' (assuming those are folders and not files)?

Maybe you should look for help in a Mac forum.

---

### Post by gordintoronto on 2010-12-19
> **ThuyT said:**
> The software I just bought (Lightroom 2.1) contains instructions to get my serial. I downloaded the sofware on my desktop and installed it. In the terminal, I wrote "chmod +x keagan", pressed enter and wrote "./keagan" and I get this message: No such file or directory.

Anybody can tell me what I am doing wrong? I am working on Mac OS 10.4.

I am not super good with computer so I need basic instructions please!! Thanks

The file is called keygen, not keagan.

---

