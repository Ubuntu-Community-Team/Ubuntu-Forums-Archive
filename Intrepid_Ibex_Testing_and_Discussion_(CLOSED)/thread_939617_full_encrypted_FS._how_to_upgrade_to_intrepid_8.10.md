---
title: "full encrypted FS. how to upgrade to intrepid 8.10?"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sblanzio on 2008-10-06
Hello everybody!
When 8.04 was released I successfully installed that using the alternate cd selecting the full encrypted filesystem.

Now, during the last monthes it always worked like a sharm, but now, with 8.10 coming, i'm getting worried about the upgrade.
Will I be able to mantain everything working without losing anything?

So what i'm about to ask is: how will I able to upgrade my encrypted disk to 8.10? I don't care about the root partition which only contains the OS but I do care about my home partition.

I know that they are all "grouped" together, so I am afraid of losing that too when i'll be installing my new ubuntu.

More, I would like to know if there is any chance to change the passphrase I enter to unlock my encrypted FS at boot time.

Thank you very much for any help!
sblanzio

---

### Post by justleen on 2008-10-06
I have the same setup on my laptop (work one, must be encrypted..). I installed it with  7.10, and upgraded when 8.04 came available.. I did create a back up of my important stuff to a backup, but in the end I didnt need it. The upgrade went fine!

About the passwd change: No idea :)

---

### Post by sblanzio on 2008-10-06
thank you for your answer.

I am worrying because usually i don't upgrade using the software updates application but I am used to burn a new cd and install everything from scratch.

I do like this because I had bad experiences with the "online" upgrade and also, this way, I'd start from scratch and I can see if the new distro version supports better my hardware.

Unluckily this time I have to face the problem of an encrypted FS, which means, I guess, I will have to burn again the Alternate Installation CD and will find some way to open my encrypted partition before starting the new installation process.

I would really like to know if this is what I really will have to do and, in such case, (if anybody knows) I also would like to change my passphrase, how this would be possible.

Of course I will prepare a good backup! :)

THank you very much again.
sblanzio

---

### Post by QCompson on 2008-10-06
I also installed 7.10 on an encrypted lvm through the alternate installer and had no problems upgrading to 8.04.  I am going to upgrade to 8.10 in the same manner once it is released and stable enough.


Here is a thread about changing the password of your encrypted disk:
[http://ubuntuforums.org/showthread.php?t=668614&highlight=encrypted+luks+change+password](http://ubuntuforums.org/showthread.php?t=668614&highlight=encrypted+luks+change+password)

---

### Post by soleblaze on 2008-10-06
I had no problems upgrading 8.04 to 8.10 on an encrypted drive.  However, my 8.04 install was about a week old and didn't have any customizations to it yet.  (such as using software from third party repositories)

---

