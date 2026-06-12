---
title: "xorg.conf help"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by abierstedt on 2007-03-02
well first off ill mention that it is a snow day here in south dakota and i am completely stuck in my house.  This is the perfect opportunity for me to set up a dual boot of ubuntu and vista.

before i even come close to this step i need to figure out how to get past that evil green line that graces my monitor every time i boot up the live cd. Of coure i know this is going to happen because i have a radeon x800 video card.  i have done a fair amount of research both on this forum and the myspace forum, and it seems this is fairly simple to fix.  I must be doing something wrong though.



these are the threads i have looked at and here is my myspace thread that also tries to help me with this issue


[x800]("http://www.ubuntuforums.org/showthread.php?t=190133")
[other x800 solution]("http://ubuntuforums.org/showthread.php?t=367358&highlight=x800")
[my thread on myspace asking  about the dual boot and the x800 configuration]("http://forum.myspace.com/index.cfm?fuseaction=messageboard.viewThread&entryID=2251487&adTopicID=6&categoryID=35&IsSticky=0&Mytoken=DDBF225A-73DD-4158-9B2D9F5E39ECA4C95159340")

this is what i have done so far

1.  booted up 6.10 and hit f6
2.  changed "quiet splash" to "break=bottom"
3.  chroot  /root  nano  /ect/x11/xorg.conf
4.  looked for the line "driver" to scroll to 
5.  nothing

after this i get stuck because gnu nano wont let me do anything.  here im supposed to change "ATI: to either "vesa" or "radeon"  and save.
i have the options to G^ get help  ^O write out ^R ect, but none of them do anything when typed and other then those options, there is nothing but a blank terminal.

i am new to ubuntu and linux based stuff for that matter, but i believe that i have done a fair amount of research for this task and i really want to get this up and running. 

i am using windows for the sole purpose of playing games and for it just being familiar to me.

this is where i am now and i really hope to be farther before i go to sleep at 3 am haha.

like i said its blizzarding out and i cant do anything so i hope that today is my lucky day to finally get linux set up on my primary pc.


i have used linux before and successfully installed knoppix and debian on other systems, but never configured internet because i didnt have access in the basement.  Now i am on a wireless connection and i have tried debian on this pc and successfully dual booted with xp, but never configured internet because my card is a pain in the but and for some reason directly connecting to CAT5 did not work with apt-get.  i recieved little help on the debian forum when i did try to resolve the issues but not alot of activitly seemed to be going on at the time, that was about a year ago.  Other than this, i have little experience and im not the greatest at commands.  


So im asking everybody that can help to do so.  i have many more issues to come once i can actually get into the dektop of the live cd, but if i can resolve this issue than the rest shouldnt be that hard

things  i see being a problem after this would be configuring wireless, dual monitor support , and having grub pick up vista ect.


ill leave it at that for now.  i can post models of hardware if asked

if i can get this working i will **donate**:) 



thankyou in advance!!

please respod i dont want to bump this that much

---

### Post by ffxr on 2007-03-02
are you sure u have got that directory structure right..?

chroot /root nano /ect/x11/xorg.conf

SHOULD BE chroot nano /etc/X11/xorg.conf

more info here: [http://www.ubuntuforums.org/showthread.php?t=367358&highlight=x800](http://www.ubuntuforums.org/showthread.php?t=367358&highlight=x800)

---

### Post by abierstedt on 2007-03-02
oh really??

yeah ill try that right now  



its just that aberry5555's posts had that as the code



ill repost  in a bit

---

### Post by abierstedt on 2007-03-03
sorry to report none of those are working, i have triple checked to make sure no  errors occur.  Any other ideas?  i downloaded the vmware trial so i can give some screenshots of some of the steps

---

### Post by abierstedt on 2007-03-04
bump

---

### Post by abierstedt on 2007-03-04
got it finally via apt get which wasnt working up until just now

---

