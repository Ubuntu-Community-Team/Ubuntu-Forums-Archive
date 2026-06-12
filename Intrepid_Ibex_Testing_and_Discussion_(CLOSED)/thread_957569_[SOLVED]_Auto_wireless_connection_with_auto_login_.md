---
title: "[SOLVED] Auto wireless connection with auto login - can it be done?"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2008-10-24
I've never been able to get wireless to automatically connect when I auto login.  I have to provide the wireless keyring every time - annoying.

Judging by the last comments at [https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247](https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247) it looks like it should be possible now, but I can't work it out.

Any suggestions, please?

---

### Post by vikrant82 on 2008-10-24
Can only be done with an empty keyring password ..

---

### Post by bcat on 2008-10-24
Actually, I don't think you need to set an empty keyring password anymore. Just go into NetworkManager and configure your wireless LAN connection as a "system setting". This avoids having to mess with your keyring, and it also has the benefit of bringing your wifi up on startup, even if you're not actually logged in.

---

### Post by gcday on 2008-10-24
until the last update broke my wifi that's what I was doing, so it's possible.

---

### Post by caryb on 2008-10-24
I don't have auto logon but I can not get my wireless to autoconnect in KDE it is a real pain & annoying.



Cary

---

### Post by caro on 2008-10-24
I've logged on to my wireless automatically since Feisty and it works now with Intrepid.  If I right click on the network connection icon in my panel and select "edit connections" it brings up a dialog box.  Select the "wireless" tab and you should see a list of the wireless connections you've configured.  Highlight the one you want to automatically log into, click "edit" and then select the box "connect automatically."

---

### Post by DavidONE on 2008-10-24
> **vikrant82 said:**
> Can only be done with an empty keyring password ..

I don't know what you mean.

> **bcat said:**
> ...configure your wireless LAN connection as a "system setting".

Just tried that but no different - I still need to enter password.

---

### Post by DavidONE on 2008-10-25
caro,

Yes, I have 'connect automatically' set.  It still asks for default keyring password every time I start up.

My default keyring password is different to my WPA2 password for wireless.  Are yours the same?

Thanks.

---

### Post by caro on 2008-10-25
DavidONE,
My WPA2 password for wireless is not the same as my default keyring password, but my login password is the same as my default keyring.  

I seem to remember having the same problem you are having with Feisty Fawn and had to install pam-keyring.  It's been a year and a half, but I found this.  It may be a place to start:  [https://help.ubuntu.com/community/WifiDocs/WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo").  Scroll down to "avoiding password nagging."

Good luck.

---

### Post by DavidONE on 2008-10-26
Thanks, caro - I read that, but it looks like things have changed in 8.10.  There is no 'pam-keyring', but there is 'libpam-gnome-keyring' which is already installed.

Looking at 'System -> Preferences -> Encryption and Keyrings' shows 'Default key: None. Prompt for a key'.  So, I guess, I don't have a default keyring password?

Looking at 'Accessories -> Passwords and Encryption Keys' shows nothing in 'My Personal Keys'.  Is this where a 'default keyring password' should be?

Or maybe it's 'Accessories -> Passwords and Encryption Keys -> Edit -> Preferences'?  There's a password keyring there called 'login'.  I tried adding 'default' but that made no difference.

'Intuitive' is not a word that springs to mind with all of this!  I've read a dozen 'how tos' on getting this working, but they all seem to be out of date and do not apply to 8.10.

Any suggestions very gratefully received.

---

### Post by GuitarRocker2562 on 2008-10-26
Doesn't it auto work if your keyring password is the same as your user password?

---

### Post by caro on 2008-10-26
> **DavidONE said:**
> Thanks, caro - I read that, but it looks like things have changed in 8.10.  There is no 'pam-keyring', but there is 'libpam-gnome-keyring' which is already installed.

Looking at 'System -> Preferences -> Encryption and Keyrings' shows 'Default key: None. Prompt for a key'.  So, I guess, I don't have a default keyring password?

Looking at 'Accessories -> Passwords and Encryption Keys' shows nothing in 'My Personal Keys'.  Is this where a 'default keyring password' should be?

Or maybe it's 'Accessories -> Passwords and Encryption Keys -> Edit -> Preferences'?  There's a password keyring there called 'login'.  I tried adding 'default' but that made no difference.

'Intuitive' is not a word that springs to mind with all of this!  I've read a dozen 'how tos' on getting this working, but they all seem to be out of date and do not apply to 8.10.

Any suggestions very gratefully received.

System > Preferences > Encryption and Keyrings has the same values as mine. (none)

When I look at Accessories > Passwords and Encryption I see the tab "Passwords."  Under that tab, there is an entry for the password to my wireless network (and others, like my password for my email, etc.)  Do you have any entries there?

---

### Post by DavidONE on 2008-10-26
> **caro said:**
> When I look at Accessories > Passwords and Encryption I see the tab "Passwords."  Under that tab, there is an entry for the password to my wireless network (and others, like my password for my email, etc.)  Do you have any entries there?

I have two:

```
Network secret for Auto phuku/802-11-wireless-security/psk
```
```
Unlock password for default keyring
```

---

### Post by DavidONE on 2008-10-26
> **GuitarRocker2562 said:**
> Doesn't it auto work if your keyring password is the same as your user password?

They are the same - I think. Although I'm now unsure that I have a keyring password - see post immediately before yours.

---

### Post by caro on 2008-10-26
> **DavidONE said:**
> I have two:

```
Network secret for Auto phuku/802-11-wireless-security/psk
```
```
Unlock password for default keyring
```

I have the  network secret for my wireless router and a passphrase for my wireless network.  It looks like you haven't saved your passphrase for the wireless.

---

### Post by DavidONE on 2008-10-26
> **caro said:**
> It looks like you haven't saved your passphrase for the wireless.

I did a clean install about a week ago and I was never given that option - and no idea how / where I would set it now.  

I've been on this too many hours today - maybe come back to it tomorrow.  Thanks for your time and help - don't hesitate if you have any more suggestions. :)

---

### Post by wgrant on 2008-10-26
You can bypass the keyring by setting the wireless as a system setting.

---

### Post by DavidONE on 2008-10-26
> **wgrant said:**
> You can bypass the keyring by setting the wireless as a system setting.

I was recommended that by 'bcat' at the beginning of this thread - tried it and it made no difference (the 'System Setting' did not stick after reboot). This time it has worked - success at last!

Thanks very much and thanks to everyone else who offered suggestions.

P.S. For those who don't know how to do this:

1. right click Network Manager icon in system tray
2. Edit Connections -> Wireless -> select your wireless connection -> Edit
3. tick 'System setting' and 'Connect automatically' if not done already

---

