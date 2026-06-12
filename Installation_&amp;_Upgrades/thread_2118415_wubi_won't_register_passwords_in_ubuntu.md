---
title: "wubi won't register passwords in ubuntu"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by mikemurray01 on 2013-02-21
Hi all,

This is my first post and I have been looking through the threads to find the solution but no luck!

I install wubi and in the screen where you set up the disk space, linux version, language etc, the username is already entered, taken from windows computer name.

I enter a password twice.

Machine shuts down to go to second phase of install.

Ubuntu boots up and a login screen appears.

I enter the username and password, but they are not recognised.

I have tried this with various passwords. I have manually changed the username to somthing simpler. I have tried to install as administrator, but always the same thing : ubuntu has not got the pre-installed passord and username, no account has been set up.

---

### Post by bcbc on 2013-02-21
> **mikemurray01 said:**
> Hi all,

This is my first post and I have been looking through the threads to find the solution but no luck!

I install wubi and in the screen where you set up the disk space, linux version, language etc, the username is already entered, taken from windows computer name.

I enter a password twice.

Machine shuts down to go to second phase of install.

Ubuntu boots up and a login screen appears.

I enter the username and password, but they are not recognised.

I have tried this with various passwords. I have manually changed the username to somthing simpler. I have tried to install as administrator, but always the same thing : ubuntu has not got the pre-installed passord and username, no account has been set up.

Hi, Welcome to the forum!

Please post the log file from the wubi install. It can be found in the %TEMP% directory and it's called wubi-xx.xx-revxxx.log (e.g. for release 12.10 it's wubi-12.10-rev273.log if I recall correctly).

You can either post it here between [CODE[SIZE="1"] [/SIZE]][/CODE] (press the # key above) or pastebin it and post the pastebin address.

Thanks

PS...
Note that Wubi automatically sets your 'display name' to be that of the Windows Account. You can change it later, but it sometimes is confusing to see a different user name. Underneath the covers the lower case name you entered (or if you accepted the default) is still used.

---

### Post by mikemurray01 on 2013-02-22
I thought I'd do a complete reinstall of wubi.exe so I deleted the old log file and wubi itself.

Installed and ran it and this time it worked!

The only difference being that I didn't click on the 'reboot now' option in wubi, just went on with other stuff until it had disappeared in a timeout, then did a full shut down and start up, not a restart.

It booted up into Ubuntu and my user name appeared on the login page for the first time.

I hope this may work for others - I've seen a few posts with similar problems.

---

### Post by bcbc on 2013-02-22
Anyone else who has this problem, please post the log file so I can file a bug, or better still file a bug yourself.
Thanks

PS the only personal information the log file contains is your Windows username and timezone location. If you don't want this public, you can search and replace the username out and obscure the location. I don't think there's anything else that would be a concern.

---

