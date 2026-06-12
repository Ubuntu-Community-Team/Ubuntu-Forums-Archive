---
title: "Restore wubi installation after windows reinstall"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by Oduig on 2011-07-04
Yesterday I decided it was time to reinstall Windows 7 because it became increasingly slow. I know that there's a different solution to solve this problem, but as a user I'm just more satisfied with the noob friendliness of Windows. However, I know that it has its drawbacks so I had a dual boot setup with Wubi (30GB).

My old configuration was as follows:
C: partition of size ~80GB with Windows 7 x64 installed
D: partition of size ~400GB with data and a wubi ubuntu at D:/ubuntu

So what I did was this:
- Backup all my personal files and D:/ubuntu on a external hdd
- Wipe the partitions using the windows installer
- Create a C: of 100GB and a D: of 380GB
- install windows 7 x64 on the C: partition

Now I would like to restore my backup of the old D:/ubuntu to a working dual boot system. I realize I may have missed some opportunities and the data may be gone, but I only found out about that when it was too late. 

I have tried installing wubi, and replacing the new ubuntu folder with the old one, but this did not work. 

error: no such device: 9054698454696DC2
error: no such disk

I have also tried replacing only the root.disk file, with the same result. I searched for other people's solutions, but they did not seem to work in my case.


Any help would be greatly appreciated, because I don't feel like setting everything up again. Especially because I'm a novice ubuntu user, this would take a lot of time for me.

Kind regards,
Guido

---

### Post by Oduig on 2011-07-04
Bumping

edit - sorry about that, many forums treat everything beyond the first page like archives. I'll refrain from bumping again. Thanks a lot for helping Rubi1200, please take your time. I noticed that you helped someone else with a similar problem [here]("http://ubuntuforums.org/showthread.php?t=1782010"). Unfortunately, the exact same trick doesn't work for me, but something similar might :)

---

### Post by Mark Phelps on 2011-07-04
Don't bump more than once every 24 hours -- it's considered RUDE to do so more frequently.

---

### Post by Rubi1200 on 2011-07-04
Hi and welcome to the forums Oduig :)

I can hopefully help you sort this out, but I have just got home from work this minute. Give me an hour or so and I will get back to this thread and walk you through the steps.

Thanks.

---

### Post by Rubi1200 on 2011-07-04
Okay, I am back.

Here is what you need to do:

you only need the root.disk you saved previously so make sure it is somewhere safe like an external medium.

Now, reinstall Wubi making sure it is the _same_ version as the version you had previously.

Install in Windows, reboot as per a fresh install and let Ubuntu finish the install at its end and then it reboots again.

Now, this is where we get stuck in:

after reboot, select Ubuntu but this time when you see the GRUB menu press "e" to edit.

Look for these lines:

*set root=(hdX,Y)*
and 
[I]linux /boot/xxxxx root=/dev/sdMY xxxx

[/I]Take a note of the values given there. For example, *set root=(hd0,3) *[I]linux /boot/xxxxx root=/dev/sda3 xxxx

[/I]Obviously, take note of the actual values for your install.

Once you have done that press Esc to return to the menu and exit by pressing "c" to get to a grub prompt and then type reboot.

Now boot into Windows and copy the saved root.disk over the new root.disk you just installed.

Once that is done reboot and go back to Ubuntu and again press "e" to edit.

Replace the values with those you noted previously e.g. if it was sda3 and now it says sda2 then change to sda3 for those lines mentioned above.

Also delete the line "search --no-floppy xxxxx"

Now you can press  CTRL+x to boot.

Once Ubuntu boots open a terminal immediately with Ctrl+Alt+T and run this command:

```
sudo update-grub
```

That should be it!

Let me know how it goes or if you have any questions before starting.

---

### Post by Oduig on 2011-07-04
Thanks millions, it worked! At first, when booting ubuntu, I thought it might have failed because it still said 'no such disk', but after a few seconds it booted anyway. Works like a charm now. 

Thumbs up for succinctness. Marked as solved :)

---

### Post by Rubi1200 on 2011-07-05
Excellent! I am really pleased this worked for you :-)

Keep a backup of the root.disk for the future and you should never have a problem.

---

### Post by Gorge09 on 2011-08-17
Ive just registered to say thanks

Ive recently made a clean install on my laptop of Win7 but Ive made a copy of my root.disk so i could keep my Wubi installation intact but managing to put the backup to work as proven allot more complicated than i thought.

But then i find this post and it worked like a charm.

Really thanks Rubi1200 you just saved me about 20GB of info and many hours of configuration.

---

### Post by theozzlives on 2011-08-17
Welcome to the forums. I don't do WUBI or Dual Boot. However, it stands to reason that you can boot the CD and replace the boot.disk with the one you want then reboot.

---

### Post by tbhatia4 on 2012-02-29
i am also stuck with this sort of issue with my first ubuntu installation ever that was a wubi
now i am using a normal installation on every other machine which i realized later that is the best method
but i wish to have the previous wubi installation back
i have tried using the normal installation but of no use as wubi is a bit different from the latter
  
i have a copy of the root'disk file but i am a  bit confused on which wubi.exe to download as i had 10.10 earlier(original installation) which i upgarded to 11.04 via upgarde manager
 after reading this thread i'm downloading a random wubi and replacing it with the desired values 
fingers crossed
i'll post here if necessary
thanks in advance

---

### Post by tbhatia4 on 2012-02-29
hello 
i did the same procedure but i'm currently stuck at the grub screen asking for the login which i remember i am typing correctly but i am unable to logon it says invalid login
kindly help me out

---

### Post by tbhatia4 on 2012-02-29
i have noted a thing that although i have downloaded the same version of wubi as i had earlier but linux image is different i have downloaded 2.6.38.8
but i previously had 2.6.38.11
i have no idea how to resolve this

---

