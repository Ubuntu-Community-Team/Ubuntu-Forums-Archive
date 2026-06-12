---
title: "Chrome and Chromium will not launch or give error, Firefox works (except for Flash)"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by Richard_Fleming on 2014-07-20
I am using the latest Xubuntu 32-bit. I just installed it and updated it yesterday.

I have tried all three versions of Google Chrome (stable, beta, unstable). Stable doesn't do anything. Beta and unstable throw up an error that my hardware isn't supported. I tried downloading the Chromium 32-bit beta [from here]("http://http://www.chromium.org/getting-involved/dev-channel") but Ubuntu Software Center said it was a bad file.

I have tried using the Software Center to install Chrome and Chromium and I've tried using Synaptic Package Manager. I also used the terminal:
[FONT=verdana][SIZE=2][COLOR=black]
[/COLOR][/SIZE][/FONT]$ sudo apt-get install chromium-browser

$ wget [https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb)
$ sudo gdebi google-chrome-stable_current_i386.de[COLOR=black][SIZE=2]b

[/SIZE][/COLOR][FONT=verdana][SIZE=2][COLOR=black]  I tried removing and reinstalling. I tried restarting. I tried fully removing. I tried removing all related stuff (flash and codecs).

Can anyone help me get Chrome or Chromium running? I need to have a recent version of Flash player working. Firefox won't play Flash at all even though I have the old version 11 installed. I have an extension to force HTML 5 on Youtube but it's of no help for other websites.

It seems really odd that such a popular program like Chrome won't even launch. Everything else I've installed so far has worked fine (TeamViewer, VLC, Skype).
[/COLOR][/SIZE][/FONT]

---

### Post by slooksterpsv on 2014-07-20
If you try to run google-chrome from terminal does it give you an error? Also what about if you try to install it via: sudo dpkg -i ./google-chrome-stable_current_i386.deb - usually after you run that you'll need to run: sudo apt-get install -f - to resolve dependency issues.

IF we could get some errors that'd be great. You can see if there's any crash report logs in ~/.config/google-chrome/Crash\ Reports

---

### Post by Richard_Fleming on 2014-07-20
When I try to launch Chromium I get a busy cursor for a while and then nothing. I tried installing version 31 and that did the same thing as 34. Upgrading 31 to 34 with Synaptics also didn't change the behavior.

There is nothing for Google Chrome in the home .config folder. There is a folder for Chromium but it's empty. I couldn't find any other.config folders. I looked in File System and turned on show hidden and didn't see anything in the main directory. I am a Linux novice.

---

### Post by Richard_Fleming on 2014-07-20
I did find something in /var/crash

_opt_google_chrome_chrome.1000.crash 1.4 MB Apport crash file

It says I have an obsolete package version installed, upgrade xdg-utils but I checked Synaptic and it says I have the latest version, 1.1.0_rc1-2ubuntu7.1

"chrome crashed with SIGILL"

---

### Post by slooksterpsv on 2014-07-20
Remove and reinstall Chrome, purge it.

---

### Post by Richard_Fleming on 2014-07-20
I got Flash working. The problem is that 11.2 and higher in Linux apparently requires sse2 and my processor is an AMD 2400+. I don't need to bother with Chrome and Chromium now. However, I will try your terminal commands just to see if that will work. I already removed Chrome and Chromium several times.

> [FONT=verdana][SIZE=2][COLOR=black]I  tried removing and reinstalling. I tried restarting. I tried fully  removing. I tried removing all related stuff (flash and codecs).[/COLOR][/SIZE][/FONT]

---

### Post by Richard_Fleming on 2014-07-21
I am now wondering if this is a bigger problem with Webkit in general. Midori is extremely unstable for me. I tried the old version that's in the repository and the latest from their website. Even doing a search with their Duck Duck Go search bar can cause a crash. Yahoo crashed in the old version on the main page when asking about HTML5 local storage. The new version just quits on pretty much anything with a complex layout. slickdeals.net is the one site that didn't crash.

Firefox continues to work fine.

I wonder if Webkit requires sse2 or something, like Flash 11+ does.

---

### Post by slooksterpsv on 2014-07-22
[https://support.google.com/chrome/answer/95411?hl=en](https://support.google.com/chrome/answer/95411?hl=en)

---

### Post by monkeybrain20122 on 2014-07-22
> **Richard_Fleming said:**
> [FONT=verdana][SIZE=2][COLOR=black]

Can anyone help me get Chrome or Chromium running? I need to have a recent version of Flash player working. Firefox won't play Flash at all even though I have the old version 11 installed. I have an extension to force HTML 5 on Youtube but it's of no help for other websites.


[/COLOR][/SIZE][/FONT]

Well it may be kind of an unconventional solution but you can get up to date (pepper) flash working in Firefox now
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

I have tested it, works perfectly on all audio and video streaming sites I tried even as a pre alpha. There are things that don't work at the moment, e.g webcam not detected and no hardware acceleration.

Another possibility is pipelight flash (Windows flash) advantage is that it can access DRM material, but I find pepper flash works more smoothly. [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

---

### Post by Richard_Fleming on 2014-07-22
Thanks for the replies [**[COLOR=#000000]slooksterpsv[/COLOR]**]("http://ubuntuforums.org/member.php?u=38762") and [**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403"). As for pepper... that's interesting certainly but I assume all Flash after 10.x isn't going to work without sse2.

---

### Post by slooksterpsv on 2014-07-22
What kind of CPU is it? Probably not Flash and Pepper require at least a P4 now which has the SSE2

---

