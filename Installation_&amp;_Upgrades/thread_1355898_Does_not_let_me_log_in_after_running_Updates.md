---
title: "Does not let me log in after running Updates"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by agargye on 2009-12-15
I recently installed 9.1 (desktop) and today ran the updates. It installed fine ... I got prompted for a restart. System restarted but did not auto-login (thats how I had it setup).

It appears to attempt the auto login but fails and prompts me to login. (which also fails). My login credentials are correct because if I enter a invalid password it states "authentication failed" but not so with the correct password. It simply returns to the login after a couple of screen flashes .... now I'm locked out without a way in!!!

How do I resolve this w/o reinstalling the O/S?

HELP!

---

### Post by munchkinmunchkin on 2009-12-15
I am having exactly the same problem.

A fresh install of 9.10 works fine without problems.

But as soon as I install the 150+ updates and then restart, everytime I log in, I keep getting returned to the login screen, I don't get an authentication failure unless I enter wrong details, so the details I'm entering are definitely correct.

My first install of 9.10 used the encrypted home directory option, and at first I thought this was the problem, so I reinstalled using the non-encrypted home directory option and still can't login after the updates.

I have done a memtest and reformatted and checked the hard disk, but still no luck.

Any help would be most appreciated.  

I have re-installed a few times using different login details but still can'

---

### Post by munchkinmunchkin on 2009-12-15
Further to my last message, the last line should read:

"I have re-installed a few times using different login details but still can't login after the updates".

BTW, the computer's spec that I am installing 9.10 onto.

Asus A7V266-E board.
Athlon 1800XP processor.
512mb of Crucial memory.
40gb Maxtor IDE hard drive.
And an old 32mb 3DFX graphics card in a PCI slot.

---

### Post by agargye on 2009-12-16
Update: I have posted a bug if you want to follow [this]("https://bugs.launchpad.net/ubuntu/+bug/497430") ... 

I did finally reinstall and ran updates again. There is definitely a bug with the updates which causes the login to fail for the primary user. Again as before I set myself up to login automatically. Login to this account fails consistently (as before) What I did do this time was before I ran UPDATES I created 2 other logins. #1 Admin (ROOT Group) and #2 another user with the same privileges as my initial login. Here's what I found ....


    1. When the login fails on the default account (created on installation) I can login as root (my Admin ac) then switch user and login with the account that is failing, successfully!
   2. In the same situation I am able to login with the 2nd user account but when I switch user and attempt to login to the default account, login fails and this time prompts me to enter the 2nd users password as if I attempted to switch to this user.


The consolation is that I am able to log in w/o having to re-install the O/S. Hopefully there'll be a fix to this soon that UPDATE will fix for me :)

---

### Post by S1gurd on 2009-12-16
Against my better judgement I gave in and let Xubuntu 9.04 upgrade itself to 9.10.  The upgrade did not go smoothly, but eventually finished.  I updated and upgraded all packages, and now-

I have the same issue.  When trying to log on as the primary user...the login screen disappears, and I see the swirling lights, then a white flash, and it is back to the login screen.  

I can login as a different user, but that helps only a little as I cannot find any hints as to where to go from here.  I will watch this thread for help.  Thanks.

---

### Post by S1gurd on 2009-12-16
I found the answer in another Forum entry.  The answer for me was:

1.Login is as an alternat user with root access.
2.read the .xsession-errors file - mine was complaining about display 0.0
3. Follow ivoshm's advice here:

remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again. 

Here is ivoshm's exact quote:

Originally Posted by ivoshm
Try switch to text console (Ctrl+Alt+F1), log in and remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again. 

That's it.  I think I am good now.

---

### Post by agargye on 2009-12-16
Update: 20091217 - The issue persists. This morning I experienced different behavior. This time non of the login's allowed me in so I rebooted and it logged right in to my default account after reboot. Something is still not right. 


Apparently I didn't need to do that either!

I had previously logged in as Admin (ROOT) and switched user to my default login. After reading S1gurd's post with the solution I decided to attempt the solution. Lo & Behold on restart my desktop logged righ into my default ac.

What ever it was fixed itself

---

