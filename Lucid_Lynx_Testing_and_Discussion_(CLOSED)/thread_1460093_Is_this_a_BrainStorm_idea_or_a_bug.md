---
title: "Is this a BrainStorm idea or a bug?"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Riffer on 2010-04-22
I am trying out 10.04, so far so good.  But I've noticed that because I've setup for auto login I get the keyring daemon coming up as soon as i get onto the Desktop.  Now I'm sure that I haven't got things setup properly etc. (if you know what I need to do here great).  What I find frustrating is the daemon doesn't tell you what app or program needs its password.  For instance my wifi needs a password which is different from other passwords, since the daemon doesn't let me know its for the wifi I get confused.

So should I pass this along to Brainstorm or file it as a bug?

---

### Post by MadCookie on 2010-04-22
> **Riffer said:**
> I am trying out 10.04, so far so good.  But I've noticed that because I've setup for auto login I get the keyring daemon coming up as soon as i get onto the Desktop.  Now I'm sure that I haven't got things setup properly etc. (if you know what I need to do here great).  What I find frustrating is the daemon doesn't tell you what app or program needs its password.  For instance my wifi needs a password which is different from other passwords, since the daemon doesn't let me know its for the wifi I get confused.

So should I pass this along to Brainstorm or file it as a bug?

This is nor a bug or a brainstorm issue...but you can make it a brainstorm issue by suggesting that the keyring does not pop up every time your wifi wants to connect.

---

### Post by madjr on 2010-04-22
papercut (usability issue)

[http://ubuntuforums.org/showpost.php?p=9150240&postcount=12](http://ubuntuforums.org/showpost.php?p=9150240&postcount=12)

---

### Post by cariboo on 2010-04-22
You should really search the forums for any problems you have with Lucid, as this issue has come up several times, and there are even threads that explain how to overcome the issue.

---

### Post by aysiu on 2010-04-22
It's already a Brainstorm:
[Idea #2393: don't ask for default keyring password if system is set to autologin](http://brainstorm.ubuntu.com/item/2393/)

It's also been filed as a bug numerous times:
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/557906](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/557906)
[https://bugs.launchpad.net/gnome-keyring-manager/+bug/236264](https://bugs.launchpad.net/gnome-keyring-manager/+bug/236264)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/486947](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/486947)
[https://bugs.launchpad.net/network-manager/+bug/34898](https://bugs.launchpad.net/network-manager/+bug/34898)
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/181281](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/181281)

It's also a papercut:
[https://bugs.launchpad.net/hundredpapercuts/+bug/518822](https://bugs.launchpad.net/hundredpapercuts/+bug/518822)

I don't see why it's so difficult. I know there are *workarounds* (you can delete the keyring password and then when prompted again, choose to have a blank keyring password, which you will be warned is "unsafe storage"). If someone sets the user to autologin, there should be no password prompt to connect to a wireless network. That's simple logical usability.

---

### Post by Riffer on 2010-04-23
Thanks for the replies.  After reading a bit I wonder if I may have setup my wifi incorrectly.  While I agree with the whole security premise, there are times when it goes overboard.  I think this is such a time.

---

### Post by Riffer on 2010-04-23
Just a bit of an update.  There is an app called "Seahorse" which is used to edit the Keyring Daemons configuration.  With this I was able to change passwords so they match.  Also I found on the pop up a tick box "use for all users".  

So there is a couple of things for people to use that has the same problem I did.

---

### Post by aysiu on 2010-04-23
Yeah, there are workarounds... I mentioned another one above (which is basically having a blank keyring password). This is still a bug, though.

---

### Post by Mr. Picklesworth on 2010-04-23
> **aysiu said:**
> Yeah, there are workarounds... I mentioned another one above (which is basically having a blank keyring password). This is still a bug, though.

Unfortunately it isn't an *easily fixable* bug, as far as I'm aware. Gnome-keyring uses a one-way algorithm to encrypt your passwords; the only way to get them out is to give it your password. So unless you want your keyring password floating about in plain text…

Of course, if someone can conjure a solution that remains secure (maybe is more secure!), protects my passwords (I also use my favourite password to log in to the WiFi network at my school via EAP-TTLS!) and is more user-friendly than the current situation, I'll be really excited! :)

---

### Post by aysiu on 2010-04-23
What do Windows and Mac do?

Isn't there a way to trigger it so that if autologin is set that the very act of logging in unlocked the keyring?

---

### Post by Riffer on 2010-04-23
Well one could argue that the security of Windows is not a model that Ubuntu should follow.  Having said that, I agree with aysiu that this is redundant.  What's the point of an auto login if you still have supply your login password.

---

### Post by SgtPepperKSU on 2010-04-23
The problem is that it isn't a matter of flipping a switch and giving you access to the keyring, where you can bypass the password (like with logging in).  The password itself is essential in being able to decrypt the keyring (encrypted so your other credentials are not directly out on the disk where anyone can read it).

The options are a) enter a password (they already do a good job of reusing your logon password for the keyring decryption when you don't auto-login), b) not encrypt the keyring, or c) put your keyring password in plaintext somewhere. Option b) doesn't sound like a thing that should be done without the user explicitly setting it that way (someone else already mentioned how to do this).  Option c) is essentially the same thing as b), but with a single layer of obfuscation.

The way I see it, this is already working as it should...  Though, perhaps a note or warning should be given when setting for auto-login, explaining this to the user, so they know to remove the keyring password if they wish.

---

### Post by Mr. Picklesworth on 2010-04-23
> **aysiu said:**
> What do Windows and Mac do?

Isn't there a way to trigger it so that if autologin is set that the very act of logging in unlocked the keyring?

Well, I don't know the technical explanation, but once I set up auto-login in Windows Vista, then changed my password a bit later. Next time I started Windows, it didn't automatically log in; it gave an angry looking "wrong password" error for its own password that it had entered automatically. (>?!)
To fix that I logged in (typed my password myself), turned off auto-login, turned it on again, and then it used my *new* password for auto-login instead of my old one.

So, apparently, it stored the password in an easily reversed format (as good as plain text) and simply typed it in for me at the login screen.

Dunno if they've fixed that in 7…

---

### Post by aysiu on 2010-04-23
I've never experienced this problem with an autologin for Mac, and I know they have a keyring also.

Perhaps if you set an autologin, there can be a prompt to use "unsafe storage" instead of the current keyring password?

---

