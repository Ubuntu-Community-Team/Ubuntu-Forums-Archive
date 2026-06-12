---
title: "Livecd. Where did the other menu options go like test for defects."
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-04-26
Just testing the RC live cd and only 2 options on menu. Install or try out.

Is there a hidden menu. I tried every key press going. Print screen included which is where the screenshot of the menu came from.

---

### Post by Elfy on 2010-04-26
[http://ubuntuforums.org/showpost.php?p=9159117&postcount=4](http://ubuntuforums.org/showpost.php?p=9159117&postcount=4)

I think that is it anyway 

[http://ubuntuforums.org/showthread.php?t=1460202&highlight=menu](http://ubuntuforums.org/showthread.php?t=1460202&highlight=menu)

---

### Post by kansasnoob on 2010-04-26
When you initially boot you'll see a screen with two emblems human = keyboard. You must press any key very quickly (it seems like 2 to 3 seconds) and then you'll get to select language followed by the old familiar options screen.

Edit: Here's the documentation on that change:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

---

### Post by -Robert- on 2010-04-26
Press the space bar when you see this screen: [http://www.unixmen.com/images/stories/ubuntu/ub1.png](http://www.unixmen.com/images/stories/ubuntu/ub1.png)
You will see more options after that.

---

### Post by uRock on 2010-04-26
> **kansasnoob said:**
> When you initially boot you'll see a screen with two emblems human = keyboard. You must press any key very quickly (it seems like 2 to 3 seconds) and then you'll get to select language followed by the old familiar options screen.

I can't find the "any key," is there another one I can hit?:lolflag:

---

### Post by philinux on 2010-04-26
I eventually have found this.

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/539172](https://bugs.launchpad.net/ubuntu-release-notes/+bug/539172)

Going down for a reboot to try this out. ;)

Why cant they put "Press any key etc etc." on the start up screen :(

---

### Post by P4man on 2010-04-26
Very stupid if you ask me.
I understand canonical wanted to simplify the menu and make it look nicer (both of which they succeeded very well) but really, one wouldnt need to have psychic powers to guess you have to press a key at the exact right moment to do anything "advanced" like testing your cd. Thats just copying the *stupid* ideas from microsoft (pressing F8 at some unknown moment to get safe mode etc). 

 Why not have an "advanced" or "more" button on there?

---

### Post by Elfy on 2010-04-26
> **P4man said:**
> Why not have an "advanced" or "more" button on there?
style and substance ... ;)

lets change things because we can - let's not tell anyone - because we can

---

### Post by philinux on 2010-04-26
From post #2 of the bug report.

> This was an intentional change at the request of SABDFL and the design team, rather than a bug. You can actually press any key (hence the
keyboard icon); it doesn't have to be Escape.

The icon at the bottom of my livecd does not look anything like a keyboard.

Mmm must invest time in my psychic training. :confused:

I did try clicking on it though.

---

### Post by P4man on 2010-04-26
> **philinux said:**
> 
The icon at the bottom of my livecd does not look anything like a keyboard.

Mmm must invest time in my psychic training. :confused:

I did try clicking on it though.

Of course someone entirely new to linux or ubuntu will understand this, were we cant figure it out :P

---

### Post by kansasnoob on 2010-04-26
> **philinux said:**
> From post #2 of the bug report.



The icon at the bottom of my livecd does not look anything like a keyboard.

Mmm must invest time in my psychic training. :confused:

I did try clicking on it though.

I'm the doofus that filed that bug report :lolflag:

That behavior changed as of the Beta1.

Something I noticed with the RC is that they now did away with the "update this installer" option which I thought was pretty cool. Now if you want to update the installer you have to boot to the Live Desktop and install the updates :(

---

### Post by philinux on 2010-04-26
> **kansasnoob said:**
> I'm the doofus that filed that bug report :lolflag:



Ah, alter ego Erick! 

How many noobs will read the release notes!

---

### Post by ranch hand on 2010-04-26
> **philinux said:**
> Ah, alter ego Erick! 

How many noobs will read the release notes!

Oh come on.  We know that everyone reads everything if they use Ubuntu.

That is why our stickies keep wearing out.

---

### Post by philinux on 2010-04-26
> **ranch hand said:**
> Oh come on.  We know that everyone reads everything if they use Ubuntu.

That is why our stickies keep wearing out.

LOL, by the way enjoy your trip. And see you with Mav Meerkat.

---

### Post by cgroza on 2010-04-26
> **philinux said:**
> I eventually have found this.

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/539172](https://bugs.launchpad.net/ubuntu-release-notes/+bug/539172)

Going down for a reboot to try this out. ;)

Why cant they put "Press any key etc etc." on the start up screen :(


They should put it in there... I think there is time coz the final release is not out yet.

---

### Post by kansasnoob on 2010-04-26
> **cgroza said:**
> They should put it in there... I think there is time coz the final release is not out yet.

The reason for emblems rather than text is because it needs to be multi-lingual. Sort of like the new road signs :)

I seriously thought it was a bug until Steve and Colin set me straight. I generally do give the release notes a fairly thorough read, but with iso-testing we're always a couple days ahead of the release notes :)

---

### Post by P4man on 2010-04-26
> **kansasnoob said:**
> The reason for emblems rather than text is because it needs to be multi-lingual. Sort of like the new road signs :)


Fair enough, keep the icon. But Im taking bets that no more than 0.1%  of all users will  deduct from that icon that they can press a key to show a menu that they can not access otherwise. 

im also taking bets 90+% of the users will be able to make such deduction if there is some simple (english) text along the icon. Heck, add Spanish and Chinese and its probably 99%.

---

### Post by philinux on 2010-04-26
> **kansasnoob said:**
> The reason for emblems rather than text is because it needs to be multi-lingual. Sort of like the new road signs :)

I seriously thought it was a bug until Steve and Colin set me straight. I generally do give the release notes a fairly thorough read, but with iso-testing we're always a couple days ahead of the release notes :)

Righto, then they need to make the keyboard icon bigger or better defined with maybe an arrow to indicate press any key.

---

### Post by kansasnoob on 2010-04-26
> **philinux said:**
> Righto, then they need to make the keyboard icon bigger or better defined with maybe an arrow to indicate press any key.

I rather wish they'd lengthen the timeout. I've done a lot of iso-testing and follow-up testing for bugs I file during such.

I swear you have maybe 3 seconds tops to hit a key! Blink or pause to discharge gas and the chance is gone :lolflag:

---

### Post by kansasnoob on 2010-04-26
I was looking and can't find it now, but I recall reading in another thread that Whiprush gathers ideas for the UDS.

Wish I could find that because I can't remember the proper method to make such requests :(

---

### Post by VMC on 2010-04-26
> **ranch hand said:**
> ...That is why our stickies keep wearing out.
This is the funniest quote of this testing phase!

Next we need the [Know Issue]("http://www.ubuntu.com/testing/lucid/beta1#Known%20issues")s to wear out.

---

