---
title: "Ubuntu first startup failure"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by theninjainurcloset on 2011-03-04
I had windows vista and its small bit of disfunctionality was not to my liking so i decided to give Ubuntu a try. I burned a cd with the installer on it and when i finished the installer it askedmme to restart and i did. I dont know if this is normal but a command looking thing came up (Sorry for my terminology) and all the commands being executed seemed perfectly normal and succesful until the end when a long list of commands saying something like "1/0 error" and then it would just sit there for hours. I typed in "-restart" and it restarted but it was unsuccesfully installed to my hard drive. Since I did the full installation it reformatted my hard drive and after a few more attempts at installation (with no functioning OS) I butned a new disc, this time using a dvd. The installation worked fine and when I rebooted, I got no error. But after it turned back on it tried to boot from my hard drive, I got a blinking underscore at the top left corner of my screen. After several more boot and installations and wipes of my hard drive, I tried to reinstall windows but since the hard drive was formatted and windows is stupid, it can't reformat the drive from the install disc that came with my dell studio, thus leaving me without any OS except for the testing enviroment booted off of the DVD and me sitting on my couch typing this post ,slightly angrily, on my iphone. Please don't leave me in the dark here guys, especially since I have a typed report I have to have finshed in 2 weeks

---

### Post by Hedgehog1 on 2011-03-05
Hello Closet Ninja!

Here is the thing - you did intall Ubuntu OK (eventually).  When you had just the blinking cursor, you were just hung up load the video driver.

So: You need to get to where your PC is booting and stopping at the blinking cursor.  You may be there right now.

Please read and follow the 'blank screen problems' thread below. 

You will be changing the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

You might need to to enter other boot parameters There are 6 of them. You may have to do them one-by-one until you get video.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

Sorry for the pain.

***The Hedge***

p.s. Why do so many folks install an OS before homework or a big paper is due?  Human nature, I guess.

---

### Post by theninjainurcloset on 2011-03-05
WOW. Thank you for the quick reply!! So I did exactly as the guide says in the link, but when I try to access the grub menu from the bios menu, it wont do anything. I dont even think there is an option to do it. I have a dell studio 1537. I boot up my computer and the dell logo comes up and I press F2 which (Im pretty sure brings up the bios menu. not good with this techie stuff :/ ) and I hold down shift. and *poof!* out of nowhere comes nothing. nothing at all besides the menu I started with. I just sit and stare at the screen with a blank expression and think to myself, " What was I doing again? " but then I remember and then I get mad and then I check the guide again on my phone (from which I am still typing from) hoping that I missed something. I've done this so many times I am pretty sure I could recite the whole thing with 100% accuracy. Even so I am very proud to announce that I figured out you can look through your hard drive from the live cd. I looked around a little at the OS and discovered something that seems q bit unusual. There are two unpacked packages (maybe 3) and there is absolutely nothing in sys. it would seem to me that something should be in sys and those packages should be unpacked, or maybe I just have no idea how linux works and nothing is supposed to be in there or theyre just all hidden or something. If any of this is any help at all for you guys to help me, then I am very glad to help you to help me to help finish my paper. Hah I made myself laugh but seriously, thank you for the help (though unsuccesful due to me or the internet or some other outside force)

---

