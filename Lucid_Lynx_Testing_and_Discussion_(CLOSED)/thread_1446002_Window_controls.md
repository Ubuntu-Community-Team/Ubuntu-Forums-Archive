---
title: "Window controls"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Emanuele_Z on 2010-04-03
Hi guys,

apparently Mark decided (ordered) to leave the buttons on the left and that's it I guess... :(
That's a sad decision...anyway he's the founder so that's it...

I'm writing here to ask if is there an easy way for the *common user* to change the setting back and move the buttons on the right.
If this way requires opening the terminal/or installing another package to have a gui to do it then please just tell me **no**.
If this is it, why has been chosen not to let the user easily fix the gui?
Is this a deliberate decision to *force* less expert users to stick with buttons on the left?

Let me know,
Cheers,

Ps. I went to System -> Preferences -> Appearances but is no obvious...

---

### Post by eluminx on 2010-04-03
The esiest way is too go to F2+alt->Gconf-editor->apps->metacity->general->button layout, choose your layout and decide how you want it displayed.  Another way to do is is also to install Ubuntu Tweak->WIndow Manager Settings and choose your desired layout.

---

### Post by howefield on 2010-04-03
> **Emanuele_Z said:**
> If this is it, why has been chosen not to let the user easily fix the gui?

I believe in the final release only Ambiance and Radiance will have buttons on the left, all you'll need to do is choose another theme, but for now you have the solutions offered by eluminx. 

> Is this a deliberate decision to *force* less expert users to stick with buttons on the left?

It is a deliberate decision not for the reason you suggest, but made with other features (as yet unknown) to occupy the space on the right.

---

### Post by forcecore on 2010-04-03
change theme to change buttons and customize, i am satisfied with current easy way change.

---

### Post by Scott82 on 2010-04-03
lol! anyone else getting completely cracked up by this stuffs? 

follow the instructions that were given to change them the other way but put in maximize,minimize,close:

---

### Post by howefield on 2010-04-03
> **Scott82 said:**
> lol! anyone else getting completely cracked up by this stuffs?

The most noise appears to be made when relatively small changes occur, like the default search engine being changed in Firefox, like buttons on the left, like pidgin being replaced and so on.

The outpouring of grief is ratcheted up several notches when compared to users not being able to boot their machines or have really serious problems.

Not that I want to minimise the impact these changes have, and to some they are obviously extremely serious, but just my 2p.

---

### Post by spyderpride on 2010-04-03
Actually its menu:minimize,maximize,close to get the old layout.

They really should make an easy setting for this in System->Preferences->Appearance... but its probably a little late to be hoping for something like that.

---

### Post by NCLI on 2010-04-03
It **is** easy, just change the theme ;)

---

### Post by Cushie on 2010-04-03
> **eluminx said:**
> The esiest way is too go to F2+alt->Gconf-editor->apps->metacity->general->button layout, 


It is easy to change back to the traditional top RHS.

Alt +F2 to open launcher

gconf-editor

select: apps/metacity/general/button_layout

Place 'spacer, after 'menu:'

menu:spacer,maximize,minimize,close

see ' post9069846 ' for full discussion.

---

### Post by Nesaskewatch on 2010-04-10
Just my two bits but...  I am liking the left side buttons.  Puts the controls where one tends to be hanging around anyway.  Besides, I run Linux to be different.  LOL  

Also, I am thinking there be new stuff comin fer the right!  Gimmee.

Cheers!

---

### Post by bash on 2010-04-10
> **btdown said:**
> Mark needs a swift kick in the nuts. There is no reason to move the stuff to the left side. NONE!

So there is this guy spending his fortune on funding a completely free and open operating system. And then he even dares to make decisions you don't like. OH NOES! How could he!

Like him or not, but it is his money he is spending, so it's his baby to decide on what to do or not. And really surprised about the tone. Don't remember reading these kinds of comments around the forum for ... actually never.

---

### Post by jpeddicord on 2010-04-10
> **NCLI said:**
> It **is** easy, just change the theme ;)

Exactly. If you want window controls moved on the right, just pick a theme that isn't Ambiance or Radiance on the first tab in Appearance Properties. They'll be set to the right.

---

### Post by Merk42 on 2010-04-10
> **bash said:**
> So there is this guy spending his fortune on funding a completely free and open operating system. And then he even dares to make decisions you don't you like. OH NOES! How could he!

So there is this guy spending his fortune on funding and one of the users doesn't like his decision? OH NOES! How could he!



Also, [good job about eliminating the infinite width of the close button, Mark](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/558327). 
Fitts' law? Who's Fitt?</sarcasm>

---

### Post by vredley on 2010-04-10
> **Merk42 said:**
> Also, [good job about eliminating the infinite width of the close button, Mark](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/558327). 
Fitts' law? Who's Fitt?</sarcasm>

Bugged: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/560118](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/560118)

---

### Post by Merk42 on 2010-04-10
> **vredley said:**
> Bugged: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/560118](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/560118)

Marked as "Invalid"

---

### Post by vredley on 2010-04-10
> **Merk42 said:**
> Marked as "Invalid"

I'm shocked. :p

---

