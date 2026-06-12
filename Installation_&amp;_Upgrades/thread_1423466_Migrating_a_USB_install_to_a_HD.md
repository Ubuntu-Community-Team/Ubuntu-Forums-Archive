---
title: "Migrating a USB install to a HD"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by alaneyue on 2010-03-06
Aloha e Kakou!  (Hello to us all!)

I am but a humble convert prostrating myself before you, the all-knowing collective.  Here is my story and my humble request...

One day, in the depths of misery evident in every Vista, I decided to give Karmic a spin.  Yet, I being mired in an insane and skewed Vista of computing life akin to looking through ***** caked Windows, was of little faith in Karmic salvation.  I needed more proof of this path to Karmic freedom.  I didn't want to abandon the relative safety of the Vista installation on my Thinkpad X200S (/dev/sda2) while learning more about Karmic salvation.  So, I bought a 16Gb SD card with the idea of installing Karmic to the SD (so I could always pop the SD out and boot via the HD).

I installed Karmic to the USB (/dev/sdb1) and configured GRUB to allow me to choose the OS that I wanted at boot time.  Well, the experience with Karmic has been ECSTATIC ENLIGHTENMENT, and now I want to but both feet in the boat and "close the Windows" for good.  That's a big step for this old dinosaur!  :-)

Something I've learned during the process is that now the SD MUST be in the laptop in order for it to boot.  If I have the SD out, the BIOS boots and when it hands off to GRUB, GRUB cannot be found and the boot halts.  This is understandable because the Karmic install is on the SD.

I've also found that when running Karmic, it likes to read from the SD a lot and that the SD is now a performance bottleneck compared to the solid state hard drive that Vista (/dev/sda2) sits on.  I'm ready to take the leap of faith.  Ideally, I'd like to take the Karmic installation (and other packages installed) and "copy" the whole thing onto the the solid state hard drive.  I know that I will have to modify GRUB if it is even possible to just "copy" the install over to the solid state hard drive.

Alas, I've searched high and low in the forums and on the internet for any kind of wisdom that some bodhisattva may have on my quest. 

And so I put my call for enlightenment out to you, the community of "Illuminati Cognoscenti", in hopes that you might feel merciful and grace this unworthy convert with any guidance or wisdom.

Me ka mahalo palena'ole (With my unbounded gratitude) for your consideration of my ha'aha'a (humble) request!

Aloha and Be Well!

Alan

---

### Post by Herman on 2010-03-07
You should be able to use your inbuilt partition program in Vista to make it shrink its own partition. You should make a backup of your files before using any partition editor.

If not you can use GParted in a Live CD or in your flash card installed Ubuntu to shrink the Vista partition and make room for a new partition for Ubuntu in your SSD. 
Make sure to remove the tick mark from the 'round to cylinders' checkbox if you do anything with a Windows Vista or 7 partition using GParted.
Windows Vista and Windows 7 partitions are not aligned on cylinder boundaries and GParted might see that as a mistake and try to move them, however, that will take an unnecessarily long time and also it will mean the boot loader will need to be informed of the move or Windows won't boot.

Create an empty partition somewhere after Windows in your SSD and make it larger than your flash memory card,  (because we can copy something from a small partition to a bigger one, but not the other way around, it won't fit).
Now you can copy the entire installation from the flash card to the new empty partition.
I would use the dd command, for doing the copying with, that's the fastest, but we need to be careful because it is quite a powerful command and will do exactly what we tell it to do. So if we give it the wrong orders we could cause ourselves some inconvenience to say the least.
If you don't trust yourself with the dd command, you can probably use Partimage or clonezilla instead. It will take longer, but that way you'll be making a backup at the same time, then copying your installation from the backup. Much slower, but safer.
Then you'd need to re-install GRUB to MBR and optionally (but recommended), give it a file system check with GParted and the job should be all done!

I can give you more details on exactly how to do some of those things if you need, or maybe someone else around here can fill in the details if I don't reply in time. I'll be back in a while.

---

### Post by alaneyue on 2010-03-07
Thanks, Hermann!

In the end, I chose to sacrifice the install on the SD.  I reasoned that the install on the SD was my first and I did a lot of "learning and playing around" on it.  I looked forward and thought that I just might be setting myself up for lots of headache trying to "go-live" on what was really a test install.

I used EasyBCD to restore the Vista MBR.  Then, I did a clean "dual boot install" on the solid state drive.  I've also documented my build for DR purposes.  I feel like this second time around I was much more rigorous with methodology. Also, my new install just screams! :-)

I am really feeling great about both the journey and destination.  I have learned a lot, and am grateful to folks like you who have freely and generously shared of their knowledge and experience.  I will pay it forward.

Aloha and Be Well!

Alan

---

### Post by Herman on 2010-03-07
:D Okay, good to hear of your success and happiness!

Solid State Drives really are nice to run operating systems in aren't they? I would imagine that would be a huge improvement over running in a flash card. :D

All the best,
Regards, Herman :)

---

### Post by alaneyue on 2010-03-08
The solid state drive was one of the best investments that I made when purchasing the Thinkpad X200S.  It continually delivers value in regards to performance, battery life, energy costs, noise, and (hopefully) longevity.

The SD was great for testing, but not for production.

Aloha and Be Well!

Alan

---

