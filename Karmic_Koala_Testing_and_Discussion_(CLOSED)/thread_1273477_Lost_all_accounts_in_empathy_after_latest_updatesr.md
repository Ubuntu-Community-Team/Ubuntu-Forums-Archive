---
title: "Lost all accounts in empathy after latest updates/reboot."
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-09-23
Is it me or others are having this issue.

---

### Post by howefield on 2009-09-23
Just updated and rebooted a few minutes ago, empathy seems fine.

---

### Post by Sophont on 2009-09-23
I just upgraded. My 3 acconts (1x GoogleTalk, 2x IRC) are still here.

---

### Post by novafluxx on 2009-09-23
Are you using the PPA version or Karmic version?

---

### Post by graaant on 2009-09-23
I'm using the PPA version, but now cannot create an account.
I create my MSN account, click "connect" and nothing happens.
I then close the window and go back in and my account is gone!?

Anyone else seen this or have any ideas?
I've completely removed all Empathy/Telepathy stuff in synaptic and reinstalled - still happens?

---

### Post by hshan on 2009-09-23
Same here.. ppa.. complete removal.. reinstall... no beans.

---

### Post by graaant on 2009-09-24
> **hshan said:**
> Same here.. ppa.. complete removal.. reinstall... no beans.

So it appears I can't create ANY accounts in Empathy at all.
As soon as the account window is closed, all accounts I made are forgotten :(

---

### Post by thomasboleyn on 2009-09-24
This is happening to me in Jaunty using the PPA version also. I'd really like to get it working so I can use these: [http://d0od.blogspot.com/2009/09/5-excellent-empathy-themes.html](http://d0od.blogspot.com/2009/09/5-excellent-empathy-themes.html)

---

### Post by rajeev1204 on 2009-09-24
Iam not using any PPA's.I just remember denying the password prompt for keyring and then an empathy welcome window popped up asking for account creation or reuse existing accounts,but the funny thing is,it didnt seem to remember any of my existing accounts.

I tried creating an msn account and clicked on connect,but no account could be created.

Now, when i start empathy it just opens empty without asking for passwords.

The .mission-control folder still has my accounts though.No idea what has happened.

---

### Post by philinux on 2009-09-24
It's probably a keyring problem. You could try this.

Delete ~/.gnome2/keyrings/login.keyring

Or check whats in the keyrings folder. It might be different than mine. I've done this before when evolution kept asking for keyring passwords.

Restart empathy. It might need you to logout and back in.

---

### Post by thomasboleyn on 2009-09-24
My problem is different to this if that is what is happening to you. I can sign in with my msn account fine on the repo version, but after upgrading to the latest PPA version so that I can use themes, the contacts box is just blank despite showing me as 'available', and from memory, I don't think that the keyring box pops up either.

---

### Post by hshan on 2009-09-24
> **philinux said:**
> Delete ~/.gnome2/keyrings/login.keyring


Did that.. no change.. no requester comes up at all for keyring. Thanks for the idea though.

---

### Post by rajeev1204 on 2009-09-24
> **thomasboleyn said:**
> My problem is different to this if that is what is happening to you. I can sign in with my msn account fine on the repo version, but after upgrading to the latest PPA version so that I can use themes, the contacts box is just blank despite showing me as 'available', and from memory, I don't think that the keyring box pops up either.


I have this issue also, but iam not using the PPA.The whole window is empty with no accounts either.

---

### Post by rajeev1204 on 2009-09-24
oook i got this worwking now, killed empathy from system monitor, killed mission control a few times, and now all accounts are back .

whoa.I think i was starting empathy over and over again as the notifier icon was missing from the panel.

I read in another thread its been moved to the indicator applet now.

Also another wierd thing is, even after quitting empathy, it seems to be running as i can still open it from the indicator applet.

Alpha software :) you have been warned.

---

### Post by hshan on 2009-09-24
Wow.. this is frustrating.. I guess i was thinking that it would be resolved in fairly short order as are most things.. ubuntu.. alpha/ beta.. or whatever. Now I'm thinking that we are a minority with this problem.. or that not that many people use empathy?..

I tried killing the empathy process.. couldn't find the mission control process running?! though checking synaptic.. it is installed.. No go for me. 

Empathy comes up with empty window.. looks like it saves prefs correctly.. but not accounts.. and no key requesters coming up what so ever. Any ideas appreciated!

---

### Post by graaant on 2009-09-24
I fail to see how this is marked as solved...

---

### Post by deathsshadow77 on 2009-09-24
Same. For some reason, my desktop works but my netbook doesnt

---

### Post by hshan on 2009-09-24
yeah.. definitely not solved!
I have had success. What I have done is take the ppa's out of the equation (empathy and telepathy), and gone with the standard karmic. I uninstalled empathy, telepathy.. and anything associated. Did a update. Installed Empathy. And, it works!

Good enough for me now.. Don't know what i'm missing without the newest (ppa's).. but hell , at least it works again!

---

### Post by deathsshadow77 on 2009-09-24
yup that seemed to fix it. I tried that before but I guess i didnt get all the packages

---

### Post by graaant on 2009-09-24
Yeah, that does it for me too. 
I wonder what's up with the PPA version?

---

### Post by rajeev1204 on 2009-09-25
> **graaant said:**
> I fail to see how this is marked as solved...


I started the thread so i definitely have the option to mark it as solved.Also iam not using the PPA as some of you are.

Iam marking this as unsolved anyway.

---

### Post by Richy on 2009-10-05
Here too, are all accounts gone. (again)
They reappeared yesterday, but now they are gone again.

Karmic - Beta Vanilla!

If that is not fixed in final Version, than it is totally inacceptable.
(I don't want starting to _pray_ to use IM everytime I turn on my Laptop)

If there is anything I can do to help, let me know.

---

### Post by cudjoe on 2009-10-26
I am using Release Candidate,

Just happened to me this morning.

Update > Reboot > Empathy not started > Start Manually > Keyring passphrase > No accounts...


Killed empathy and mission-control > Start Manually > All accounts here.

---

### Post by braingram on 2009-10-26
I was having this problem with the beta and upgrading to the rc did not fix it. I've tried killing and then restarting empathy but it does not seem to fix the problem.

How do I go about restarting mission-control?

---

