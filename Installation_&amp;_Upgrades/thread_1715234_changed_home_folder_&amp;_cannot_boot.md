---
title: "changed home folder &amp; cannot boot"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by reqqq on 2011-03-26
firstly is my first post in here & have to say many thanks to this  perfect ubuntu forum-i am trying to read first and then post something  .after a year of reading i did something so stupid as i see now and i  want your knowledge on something 
i wanted to expand my disc space using an sd card and did this 

sudo mv /home/name_of_home_folder  home/name_of_home_folder_bk 
sudo mkdir /home/name_of_home_folder 
sudo mount /dev/sdXX(sd card) /home/name_of_home_folder 

after this i cannot boot says cannot boot ,nautilus cant find home folder etc &more
after doing alt-ctrl-f1 and doing login i can find my old home folder with all inside 
the point is how i can change to my old home folder -have to find the solution  in order not to do format again :smile: i use ubuntu desktop edition on an acer aspire one netbook with ssd 8gb -
please help

thanks oldfred
as oldfred said have to setup fstab ,i agree i saw some threads with this but how this can be done?
thanks in advance

---

### Post by Hedgehog1 on 2011-03-26
Here is a nice tutorial on doing this (I used it myself about a month ago to do the very same thing):

[Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

The examples use ext3 as the format, you may be using ext4.

***The Hedge***

:KS

Here is what you are doing:

[IMG]http://img863.imageshack.us/img863/6315/netbooksd.png[/IMG]

---

### Post by reqqq on 2011-03-26
well thanks but i think this is not the solution for now we forget the sd card for now-i want to bring back my home folder i did a backup as i mentioned above -i receive error on booting and while i am in the desktop screen without nothing visible i sign in as root with alt+f2 and i can see my folder i did a backup .how can i bring it back for normal boot?well sorry but i confused a little bit

also when bootin says could not update iceauthority file /home/nameofhomefolder/.iceauthority
problem with the configuration server /usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256
nautilus could not create the required folders /home/nameofhomefolder/desktop , /home/nameofhomefolder/.nautilus.

and then i am on the desktop without visible anything

---

### Post by reqqq on 2011-03-26
i think i fixed the problem following this thread [http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
but now i can see in my home folder a folder with the name of my ex name of home folder(which is actually the same name )  which has all the things i had inside icluding documents downloads ,all. is it proper to copy the folders from this folder to my now home folder or should i do something else or should i leave as it is? the point is that all work fine as i can i see till now-i am surprised!!!

---

### Post by Miljet on 2011-03-26
On your original move command you left out a slash before the second home.
> sudo mv /home/name_of_home_folder home/name_of_home_folder_bk 

Should have been:
sudo mv /home/name_of_home_folder /home/name_of_home_folder_bk

---

### Post by reqqq on 2011-03-27
guys thank you all for the answers ,fast and reliable-i think i will start asking on this forum :) i was truing to read first but sometimes you read too much & then you are confused sometimes-i think i fixed my problem for now & now i am trying to add an sd card so as to expand my storage -ok this how should be done ?is there any instructions?i think i should follow the tutorial Hedgehog1 already posted?if there is any other post with more instructions plz let me know -i will search again but i did not find anything else
thanks in advance

also something else if there is a thread showing how you can backup your all system so as if i need format my netbook next time not have to do all the installation again & waiting for the updates & all of the programms installed -can this be done on a usb flash?

---

