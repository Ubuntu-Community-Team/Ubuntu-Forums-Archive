---
title: "[SOLVED] how to install Bootsplash in Kubuntu"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by LitusMayol on 2008-01-28
Hi everyone!

I've downloaded a bootsplahs from KDE-looks that i really like, is  called "Linux-Boot-Splash". Search it on  **Contents/Bootsplsh Screen**.

Ok, so i don't know anything what i've to do. I've downloaded the archive, but don't know how to install it.Any help?


Sorry, i'm a newbie. 
Lot of thanks!

---

### Post by LitusMayol on 2008-01-28
While i don't know hot to install it, i've downloaded this one:

[http://www.kde-look.org/content/show.php/Ubuntu+7.04+Grub+Bootscreen?content=57961](http://www.kde-look.org/content/show.php/Ubuntu+7.04+Grub+Bootscreen?content=57961)

And tried to put it on. But i don't understand this orders:

> #the following is used to change the screen colours when splashimage is used
# Set text color to RRGGBB
foreground FFDE93

# Set shadows and selected highlight to RRGGBB
#this is NOT the screen background but the text shadow
background FE5C00

i'd rather prefer the other, but while i can't i try with this.

---

### Post by Partyboi2 on 2008-01-28
you could try something like startupmanager to get it setup
to install
```
sudo apt-get install startupmanager
```
Or you could have alook [here]("http://users.bigpond.net.au/hermanzone/p15.htm#splash")

---

### Post by LitusMayol on 2008-01-28
It works, so thank you. 

But the startupmanager allows e to customize the bootsplash, but not to put my first option, neither the second one. 

So, thanks, because its a temporary solution, but i want to have the first post's boot splash, and i don't know if startupmanager can do it (if it can, i don't know how)

thanks anyway!

---

### Post by Partyboi2 on 2008-01-28
1. Download the Linux-Boot-Splash.
2. unzip the tar file by double clicking and choosing extract
3. Start startupmanager
4. Select 2nd tab (Appearance)
5. Under bootloader themes make sure "Use background image for bootloader menu" is ticked.
6. click on "Manage bootloader themes"
7. click on "add" 
8. Move to the directory where you have download "Linux-Boot-Splash" (you will need to navigate to your home folder from root. eg. if linux is on your Desktop
```
/home/username/Desktop/linux/images
```*****Change username to your login name

9. choose either "bootsplash-1024x768.jpg"
or
"silent-1024x768.jpg" press "close"
10. Now select from "Grub background images" the theme you want to use then "close" and
11. reboot.

---

### Post by LitusMayol on 2008-01-29
Fantastic!

Now i can have 1 of  the pictures! ;) thanks! But, the first think that appears on my computer in the moment ii get it on, is a "CompaQ" image (my computer is a Compaq). Can i change this image for the other one i've downloaded and not using now? 

Thanks!! ;) (how can i thank you in the way it appears in your profile i want it! because u really helped me)

---

### Post by Partyboi2 on 2008-01-29
>  Thanks!! :wink: (how can i thank you in the way it appears in your profile i want it! because u really helped me)the star medal next to the quote button under profile
                      [[IMG]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/IMG]]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=4223823")                                                                     [[IMG]http://ubuntuforums.org/images/uf/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=4223823")                                           [[IMG]http://ubuntuforums.org/images/uf/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=4223823")                                           [[IMG]http://ubuntuforums.org/images/uf/buttons/quickreply.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=4223823")
I think there is a setting in the bios to turn the compaq startup logo off. Should be able to get into the bios by pressing F10 at startup.

Edit: Yes you can change the image all you have to do is repeat the steps above to add that Bootsplash image to startupmanager.

---

### Post by LitusMayol on 2008-01-29
hi again (you've been thanked xD)


> I think there is a setting in the bios to turn the compaq startup logo off. Should be able to get into the bios by pressing F10 at startup.

Edit: Yes you can change the image all you have to do is repeat the steps above to add that Bootsplash image to startupmanager.


Yes i supose by pressing F10 i can switch it off, i'll try then. But what i meant with changing the image was, if i can change the Compaq's images for the "silent" image. Because id' like to put "silent"image while Compaq, and "bootsplash"image during the time i've to choose OS.

Thanks again man! ;)

---

### Post by Partyboi2 on 2008-01-29
I am not sure if you can swap the compaq image I think that is part of the bios setup. I could be wrong and maybe someone else might know.
Thanks for the thanks, just happy to help :)

---

