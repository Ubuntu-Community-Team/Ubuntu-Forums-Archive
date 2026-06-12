---
title: "boot order..."
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by dedemith on 2010-04-07
I use dual OS, n i have a problem when i want to set boot order. Can i change boot order? or can i make a priority for my OS?

---

### Post by Cavsfan on 2010-04-07
Are you using grub 2?

---

### Post by Cavsfan on 2010-04-07
If you are either on Jaunty or Karmic you are using grub 2. 
Enter this "sudo gedit /etc/default/grub"
and change GRUB DEFAULT=1 to what ever number you need.

Make sure this is not commented out:
GRUB_TIMEOUT=30 and set the number in seconds to what you desire.

---

### Post by Cavsfan on 2010-04-07
Oh, I forgot, run "sudo update-grub" after any changes are made.
Or else they will not take effect.

---

### Post by dedemith on 2010-04-07
wow...

well done...

thanks 4 giving me the solutions.. GBU...

---

### Post by dedemith on 2010-04-07
> **Cavsfan said:**
> If you are either on Jaunty or Karmic you are using grub 2. 
Enter this "sudo gedit /etc/default/grub"
and change GRUB DEFAULT=1 to what ever number you need.

Make sure this is not commented out:
GRUB_TIMEOUT=30 and set the number in seconds to what you desire.

 1 more question, what must i do if there are trouble while i run the command, for example, "GRUB_TIMEOUT=30 and set the number in seconds to what you desire"..

---

### Post by Cavsfan on 2010-04-07
> **dedemith said:**
> 1 more question, what must i do if there are trouble while i run the command, for example, "GRUB_TIMEOUT=30 and set the number in seconds to what you desire"..

That is just in the same file where the default is.
If you want it to display the menu for 30 seconds before automatically taking the default,
you can put 30 in there. That is what I have mine set to. 30 seconds is more than enough time.

I bootup and if nothing is done in 30 seconds it automagically goes into the default OS.

---

### Post by Cavsfan on 2010-04-07
Once you get familiar with all of this and since your dual booting, you can customize your boot up screen by looking 
at this thread in this forum: [COLOR=Blue]_[http://ubuntuforums.org/showthread.php?t=1296225](http://ubuntuforums.org/showthread.php?t=1296225)_[/COLOR] 

I currently have mine set to a beautiful 1920x1200 version of this picture:

[[IMG]http://img686.imageshack.us/img686/3706/beautifulboatfillingwit.th.jpg[/IMG]]("http://img686.imageshack.us/i/beautifulboatfillingwit.jpg/")

It is a little bit complicated, but it's not too bad. 
The more you learn the easier it will become. Ubuntu is awesome! :guitar:
And you can always depend on someone here to help.
I am the least knowledgeable as I have only been using Ubuntu for almost a year, but 
a lot of people here really know their stuff and are very generous in sharing knowledge.
That is what makes Ubuntu so great!

---

### Post by dedemith on 2010-04-08
ok.. thanks...:):):)..

nice info...

---

