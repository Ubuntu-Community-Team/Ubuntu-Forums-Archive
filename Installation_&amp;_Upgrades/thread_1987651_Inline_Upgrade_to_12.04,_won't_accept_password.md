---
title: "Inline Upgrade to 12.04, won't accept password"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by BlackFireNova on 2012-05-26
Help!

My Ubuntu installation was working fine, but today I was offered an inline upgrade to version 12.04.   I thought, sure why not.

The upgrade completed, and now I am at the primary login screen.  Very FRUSTRATING, the system will allow me to go in as a GUEST (which in my previous version was locked OFF), however it will NOT recognize me to login under my account, with the SAME PASSWORD as I used for the account BEFORE I allowed the inline upgrade.  SAME PASSWORD!!!  

Why the bloody blue blazes is my password no longer recognized, and why the dickens is the GUEST account accessible?  What madness is this, and how do I FIX IT??

(If I end up having to reinstall I PROMISE I will be going to Mint!  The only thing that has stopped me from trying it is that Ubuntu was working fine.)

There is NO EXCUSE for offering an upgrade that CHANGES THE PASSWORD, that is just plain stupid!

Anyone have any idea why this happened, and how to fix it?

Thanks

BlackFireNova:confused:

---

### Post by HalfNote5 on 2012-05-26
> **BlackFireNova said:**
> Help!

My Ubuntu installation was working fine, but today I was offered an inline upgrade to version 12.04.   I thought, sure why not.

The upgrade completed, and now I am at the primary login screen.  Very FRUSTRATING, the system will allow me to go in as a GUEST (which in my previous version was locked OFF), however it will NOT recognize me to login under my account, with the SAME PASSWORD as I used for the account BEFORE I allowed the inline upgrade.  SAME PASSWORD!!!  

Why the bloody blue blazes is my password no longer recognized, and why the dickens is the GUEST account accessible?  What madness is this, and how do I FIX IT??

(If I end up having to reinstall I PROMISE I will be going to Mint!  The only thing that has stopped me from trying it is that Ubuntu was working fine.)

There is NO EXCUSE for offering an upgrade that CHANGES THE PASSWORD, that is just plain stupid!

Anyone have any idea why this happened, and how to fix it?

Thanks

BlackFireNova:confused:

Question:  Have you been able to su or sudo under the guest account?  If so, why not try changing your password (from inside the guest account) back to its original state.  

Haven't had that happen to me, personally, but it sounds awful.  On the up-shot, if all else fails you can do what I did when my poor little lappy (AAO netbook) crashed -  use a live-cd coupled with ```
sudo nautilus
``` (or, y'know, su thunar, if you're an XFCE fan) to grab all your stuff - maybe toss it over the network to another comp, or use a USB connex and copy it to a backup drive or something.  

Then you can dump it all back in place when the new OS is reinstalled.   Oh, and while I am a huge fan of Ubuntu, I have to say that you might enjoy Mint. It's based on Ubuntu quite closely, so you can use Ubuntu repositories without much ado, and there's virtually no learning curve.  Either way, good luck with it.  I had an upgrade go wrong recently, and it's never fun.

---

### Post by bogan on 2012-05-27
Hi!, [B]BlackFireNova,
[/B]
When you enter your username password in the login script box, does it show 'incorrect password, try again' or switch to a black screen and back to the login screen without any message?

If the first, boot to recovery, select' fsck' to reset from 'Read Only' to 'Read/Write'; then drop to root terminal,  - you should not need to login or enter a password - and run: ```
passwd `username`
``` follow prompts to reenter your wanted password twice, and reboot.

If it does not work Post back what happens.

Chao!, **bogan.**

---

### Post by redmantripper on 2012-05-29
> **bogan said:**
> Hi!, [B]BlackFireNova,
[/B]
When you enter your username password in the login script box, does it show 'incorrect password, try again' or switch to a black screen and back to the login screen without any message?

If the first, boot to recovery, select' fsck' to reset from 'Read Only' to 'Read/Write'; then drop to root terminal,  - you should not need to login or enter a password - and run: ```
passwd `username`
``` follow prompts to reenter your wanted password twice, and reboot.

If it does not work Post back what happens.

Chao!, **bogan.**

Hey can you help me out with the second problem? I just installed 12.04 and I'm dual booting with Windows 7. 

At first, I thought I had simply forgotten my password, so I went into recovery mode and reset my password. When I tried to log back in, using the incorrect password would cause the system to ask for the correct password (as expected) but using the correct password would cause the system to switch to a different screen, where it would show some messages that would be visible for a fraction of a second before switching back to the log in screen (no time at all to read what any of the messages said). 

Any advice? Thanks!

I went back and got the error messages:

[I]Stopping save kernel messages
mountall disconnected from plymouth


[/I]

---

### Post by bogan on 2012-05-29
Hi!,** redmantripper**,

It is difficult to give specific advice as it depends on having more info as to what access you have - or do not have.

In my case, I searched the Forums and google, finding half-a-dozen suggestions, none of which worked. Finally I realised I had a full backup of my home folder, copied it back and everything was OK.

But then I do not suppose you have that option.

So my first suggestion is:

Edit: Afterthought: 
Does it make any difference if you try to log-in to ubuntu 2d, or to Gnome -Classic-No-Effects ??

Please Post details of what access you** DO** have; eg can you login as guest? or after pressing 'Ctrl+Alt+F1' ? did you login from recovery or did that not need a password ?

In my case I could login as guest but after I gave it a Password I could no longer do so, but still could with a Guest session to a default ubuntu screen.

Second: 
Searching these Forum gave me multiple ideas including: 

Renaming the ~/.Xauthority file, or altering its permissions - try:```
cat ~/.Xauthority   #or 
ls -l ~/.Xauthority  # this should give "-rw------- 1" at the start.
```And renaming the various ~/ settings files: .gmome, .gconf, .local and .compiz

Plus of course resetting unity, re-configuring gnome and compiz etc etc.  There is no shortage of ideas, but I am not able to recommend any particular one:  all I can say is that none of them seemed to make things any worse, even if they did not make things better either.

Best of luck,

Chao!, **bogan.**

---

### Post by redmantripper on 2012-05-29
> **bogan said:**
> Hi!,** redmantripper**,

It is difficult to give specific advice as it depends on having more info as to what access you have - or do not have.

In my case, I searched the Forums and google, finding half-a-dozen suggestions, none of which worked. Finally I realised I had a full backup of my home folder, copied it back and everything was OK.

But then I do not suppose you have that option.

So my first suggestion is:

Edit: Afterthought: 
Does it make any difference if you try to log-in to ubuntu 2d, or to Gnome -Classic-No-Effects ??

Please Post details of what access you** DO** have; eg can you login as guest? or after pressing 'Ctrl+Alt+F1' ? did you login from recovery or did that not need a password ?

In my case I could login as guest but after I gave it a Password I could no longer do so, but still could with a Guest session to a default ubuntu screen.

Second: 
Searching these Forum gave me multiple ideas including: 

Renaming the ~/.Xauthority file, or altering its permissions - try:```
cat ~/.Xauthority   #or 
ls -l ~/.Xauthority  # this should give "-rw------- 1" at the start.
```And renaming the various ~/ settings files: .gmome, .gconf, .local and .compiz

Plus of course resetting unity, re-configuring gnome and compiz etc etc.  There is no shortage of ideas, but I am not able to recommend any particular one:  all I can say is that none of them seemed to make things any worse, even if they did not make things better either.

Best of luck,

Chao!, **bogan.**

Thanks for the reply. I ended up just reinstalling 12.04 since the issue started right after installation, no need to worry about losing/backing up files from my account. 

Before the reinstall, I was able to get on my guest account. I also had access to my admin account via CTRL-ATL-F1 with the password I set via recovery mode.

---

