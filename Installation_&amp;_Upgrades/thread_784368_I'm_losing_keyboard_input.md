---
title: "I'm losing keyboard input"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Auximenes on 2008-05-06
As a student of Japanese language, tinkering with SCIM for Japanese input has been a central part of my Ubuntu experience, and a few weeks ago I also managed to get SCIM to work in applications such as aMSN and SKYPE.

However, in aMSN, eventhough Japanese input works like a breeze, I quite often lose keyboard input totally. For example, when I open a chat window, I can write until the other person joins the conversation, where at that point I lose keyboard input and is unable to type anything, before I ALT+TAB out of the window and into it again, minimize the window and maximize it again, or similar.

If that isn't annoying enough, keyboard input also disappears when people log on and even when I'm chatting in one window and another person is writing to me in another open chat window.

Worst of all is when I'm chatting in an open window, and a new person initiates a chat with me, e.g. starts a new window, at which point I lose input totally, and has to restart aMSN to be able to actually write something.

I just upgraded to 8.04, and I'm wondering if that could have any influence

Any suggestions/solutions/ideas would be much appreciated ^^

---

### Post by kalumba on 2008-07-05
I have the same problem, but it also happens when I am using English letters.

Someone comes online. Keyboard input stops. Alt+Tab fixes it
Someone goes offline. Keyboard input stops. Alt+Tab fixes it
Someone changes status. Keyboard input stops. Alt+Tab fixes it
I get back from away or whatever. Keyboard input stops. Alt+Tab fixes it
I change status. Keyboard input stops. Alt+Tab fixes it
Sometimes it also stops accepting input from the keyboard when I switch between apps on the virtual desktop.
Right now, as I am writing this, the input also froze in Firefox and even though the cursor was blinking it did not respond to key strokes. While aMSN is very much affected by this problem it also happens in other programs such as Pidgin. I am using Ubuntu 8.04 and I would really like to know what the problem is and a fix/workaround as soon as possible.

PS
Upgrading manually to aMSN 0.97.1 did not solve the problem. Neither did manually upgrading to Pidgin 2.4.3.

---

### Post by aniketvb on 2008-07-08
Even I have the exact same issue with scim and M17N Hindi Phonetic Input. Please find a solution . .. .anyone!!

---

### Post by findspiderweb on 2008-07-10
I've had this problem before too. This is caused by bug #66104. 

Here's the link to the bug report
[https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104)

The fix:
1. Exit scim (right-click the scim icon, click on exit)
2. Open the /home/yourname/.scim/config file
3. replace "/FrontEnd/X11/Dynamic = false" with "/FrontEnd/X11/Dynamic = true"
4. Restart scim (log out and log back in)

---

### Post by kalumba on 2008-07-27
> **findspiderweb said:**
> I've had this problem before too. This is caused by bug #66104. 

Here's the link to the bug report
[https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104)

The fix:
1. Exit scim (right-click the scim icon, click on exit)
2. Open the /home/yourname/.scim/config file
3. replace "/FrontEnd/X11/Dynamic = false" with "/FrontEnd/X11/Dynamic = true"
4. Restart scim (log out and log back in)

This work around locks scim into the other foreign language mode (Chinese) and refuses to honor the switch (CTRL+Space Bar) to English keyboard so it was a no go for me. The other proposed solution on the same website:

If you do not use any programs linked to libstdc++5 (very few of the Ubuntu official packages do, one know exception is the fglrx video driver for ATi cards; but plenty of third-party programs do, such as firefox downloaded from [www.mozilla.com](www.mozilla.com), and Adobe's PDF reader), you can use the scim-immodule setting in im-switch. To change the im-switch setting, just run "im-switch -s scim-immodule" command.

Did not work for me either. When removing libstdc++5 it also wants to remove the w32codecs so you can't watch videos encoded with Microsoft codecs and others. I have decided to use Pidgin instead as it is not as affected by this as aMSN until a solution comes along.

---

### Post by anjie on 2008-10-19
Hello!

have you fixed the problem? I'm really fed up with it. With pidgin I have no problem at all. I use Chinese input too, so I can't use the first workaround.

Thanks

Anjie

---

