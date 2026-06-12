---
title: "Password Retrieval"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by donaldshelton on 2008-10-12
I just downloaded and installed the beta 8.10

I can log into the system, but when I start the update manager, it refuses the password.

I assume the password is the same for the update manager as it is to log on?

If not, how do I retrieve the necessary password to do administrative tasks?

---

### Post by EdThaSlayer on 2008-10-12
Try this:

type your password in Gedit or a similar text program.

Then ctrl-c and when the synaptic pop comes to ask for your password just ctrl-v.


Usually it's just the mistyping that occurs that creates these types of problems.

---

### Post by donaldshelton on 2008-10-12
> **EdThaSlayer said:**
> Try this:

type your password in Gedit or a similar text program.

Then ctrl-c and when the synaptic pop comes to ask for your password just ctrl-v.


Usually it's just the mistyping that occurs that creates these types of problems.
I tried this, but to no avail.

Any other thoughts??

---

### Post by sinclair86 on 2008-10-12
are you getting any errors? if you arent check ur caps key...

---

### Post by donaldshelton on 2008-10-12
> **sinclair86 said:**
> are you getting any errors? if you arent check ur caps key...
The only error message I get is incorrect password.


And yes, I checked the cap lock key.

Don

;)

---

### Post by adityakavoor on 2008-10-12
System > preferences > About me > Change password

Log off and login and try

---

### Post by tommcd on 2008-10-12
See this to reset the password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by petteriIII on 2008-10-12
I have exactly the same problem. In my opinion it has something to do with language- and country settings. I tried many things but nothing helped. Then I changed my password (I changed it with LiveCD) to something that has only english letters and numbers. It helped but left me furious.

---

### Post by pveith on 2008-10-12
If this happens again: The reason for this is probably that your gdm uses another keyboard-layout than your gnome-session.

Try entering you password in the login name in gdm (login-screen) to see which characters it actually contains. The easiest way to change this behaviour would be to change keyboard-layout directly in xorg.conf to make the gdm layout identical to your gnome-session layout.

By editing key in section Section "InputDevice" with Identifier "Generic Keyboard", you should be able to change this behaviour.
Keys to edit are probably: "XkbModel" and "XkbLayout".

---

### Post by plun on 2008-10-12
For me this looks like a rather ugly bug for non-english settings.

Any filed ?

[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=gnome-settings&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=gnome-settings&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by petteriIII on 2008-10-12
> **pveith said:**
> If this happens again: The reason for this is probably that your gdm uses another keyboard-layout than your gnome-session.

Try entering you password in the login name in gdm (login-screen) to see which characters it actually contains. The easiest way to change this behaviour would be to change keyboard-layout directly in xorg.conf to make the gdm layout identical to your gnome-session layout.

By editing key in section Section "InputDevice" with Identifier "Generic Keyboard", you should be able to change this behaviour.
Keys to edit are probably: "XkbModel" and "XkbLayout".

Thanks o'bunch, this made things operate allright.:)

---

