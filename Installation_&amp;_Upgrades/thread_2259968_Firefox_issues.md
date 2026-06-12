---
title: "Firefox issues"
date: 2015-01-08
forum: Installation &amp; Upgrades
---

### Post by roland_burley on 2015-01-08
Hi - real newbie to Ubuntu/Linux but trying to learn.

I had Firefox installed but was having problems with the Flash Player plugin and could not get it to update no matter what I tried. So I thought I would be clever and nuked Firefox with the intention of re-installing it to see if that helped. When I tried 'sudo apt-get install firefox' I kept getting error messages about various files/repositories(?) not being available. When I tried a direct Mozilla download I kept getting multiple warnings about downloading from unauthenticated sources or warnings about my internet connection (which seemed fine otherwise) and/or the same error messages about files not being available. I ran a check following advice elsewhere on the forum and Firefox is not installed (although I do seem to have a folder with what looks like containing many of the required files including Chromium(?). Also every time I try to run Ubuntu One it just hangs ('Getting information, please wait').

I know the internet connection is not an issue because I am using a lap top to post this message (quod ergo, etc.)

Any suggestions about what I did wrong and/or how to fix it would be gratefully received 'cos I'm stumped.

RAB

---

### Post by roland_burley on 2015-01-08
Oh - and I am running Ubuntu 13.04 and get exactly the same problems when I try to download Chromium from the Ubuntu Software Centre as I do when I try to download Firefox from the same place ('Failed to download repository information. Check your internet connection')

---

### Post by kpatz on 2015-01-08
13.04 is no longer supported, so the repositories for it no longer exist.

I'd recommend upgrading to 14.10 or 14.04 LTS.  14.04 LTS is supported for 5 years so that's what I would recommend.  The non-LTS versions are only supported for a short time.

---

### Post by roland_burley on 2015-01-08
Ahhhh that would explain it. Thanks.

---

### Post by Impavidus on 2015-01-08
Upgrading would go via 13.10, which is no longer supported. Try a clean install of 14.04 instead.

To install flash on firefox, the easiest way is to install the package **flashplugin-installer** from the software centre.

---

### Post by roland_burley on 2015-01-08
After a bit of a faff I have the upgrade running. Still doesn't explain why it didn't update automatically as I had it set. I have only been running this install for a few months so I cannot work out why I am so far behind the curve. Thanks for all the help.

RAB

---

