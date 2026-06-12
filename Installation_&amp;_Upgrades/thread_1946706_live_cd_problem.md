---
title: "live cd problem"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by petalotis on 2012-03-25
hello,

i am trying to install ubuntu in my laptop. Live cd and live usb boot normally but when i click try ubuntu or install ubuntu the system stuck. Also i remove the hard disc and try other live cd like gparted  but i took the same results.

from live cd i get black screen 

from live usb i get this output and remain in this forever

[IMG]http://dc120.4shared.com/img/DiZ3eU2n/s3/24032012538.jpg[/IMG]

any ideas ?

*edit: is there any way which i can install ubuntu in seperate partition from inside the windows ?

thanks

---

### Post by mörgæs on 2012-03-25
Have you tried the alternate ISO for installing?

---

### Post by petalotis on 2012-03-25
i have tried -ubuntu 10.04 lts 
             -ubuntu 11.10 
             -ubuntu 9.04 (just curious)
             -gparted
             -lubuntu 11.10 

from live cd and usb nothing worked 

except windows 7 tragic :P:P:P

*to mention this live cd or usb first i try to another laptop and work perfectly

---

### Post by petalotis on 2012-03-25
yes juat try the alternate cd and again system stuck black screen

also i get into command line install and  took black screen

thanks for your reply

---

### Post by mörgæs on 2012-03-26
Which screen card do you use?

Boot options might do the trick for you:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by cmavr8 on 2012-07-03
He can't even get there!

Petalotis, can you try another linux distro, like puppy linux and see what happens? If it does not boot, does it give the same error as Ubuntu?

Good luck (with your exams too)

---

### Post by petalotis on 2012-10-15
i try puppy linux and open suse 12.2 still the same problem wtf 

in open suse arrive in the menu which can select try open suse and after black screen

---

### Post by cmavr8 on 2012-10-15
Looks like it's the same thing, linux can't boot on your machine.

Do you still have windows? You could try installing linux through win, as you suggested in your first post...

---

### Post by mörgæs on 2012-10-15
Please give a complete hardware description.

As mentioned before boot options are worth trying.

---

### Post by Bashing-om on 2012-10-15
This guide will prove useful for the boot options:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)
[INDENT]hth <==BDQ

[/INDENT]

---

### Post by petalotis on 2012-10-16
thank you very much for your replies 

wubi installation give me black screen i cant into ubuntu

system oveview :


[http://i1187.photobucket.com/albums/z394/petalot1s/Capture1_zpsb5265b0a.png]("http://i1187.photobucket.com/albums/z394/petalot1s/Capture1_zpsb5265b0a.png")


i try the options of that tread with black screen

options nomodeset and nolapic give me black screen 

and acpi=off give the follow image screen

[http://i1187.photobucket.com/albums/z394/petalot1s/20121016_104602_zps879c2d5a.jpg]("http://i1187.photobucket.com/albums/z394/petalot1s/20121016_104602_zps879c2d5a.jpg")

---

### Post by mörgæs on 2012-10-17
I guess this thread is your best option:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

