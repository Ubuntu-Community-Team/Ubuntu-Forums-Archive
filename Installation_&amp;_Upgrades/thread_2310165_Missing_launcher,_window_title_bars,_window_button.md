---
title: "Missing launcher, window title bars, window buttons and icons after 15.10 upgrade"
date: 2016-01-16
forum: Installation &amp; Upgrades
---

### Post by kevin203 on 2016-01-16
Hello everyone, Im new in the forum and beginner in linux systems. I had installed ubuntu 15.04 in a dell inspiron 4110 laptop. Some days ago I upgrade ubuntu to the 15.10 version, when the system is restarted, all was ok in the "login window" but when I enter to my account (or guest account) the top bars ( previously visible in the login window) disappears and the launcher never start, the desktop icons like files and folders appears with a blank icon and if I open a new window, terminal, or any program, it appears without title bar, then I can't move,close or maximize it!

Login window image:
[http://s12.postimg.org/owelkxrkt/20160116_155413.jpg](http://s12.postimg.org/owelkxrkt/20160116_155413.jpg)

Desktop image with my stycky notes sofware started, no launcher, no top bar, and missed icons:
[http://s16.postimg.org/kxfx4kjmt/20160116_155508.jpg](http://s16.postimg.org/kxfx4kjmt/20160116_155508.jpg)

Folder open with missed bar and icons:
[http://s30.postimg.org/b7f2nvbcx/20160116_155530.jpg](http://s30.postimg.org/b7f2nvbcx/20160116_155530.jpg)




I had reading many similar post in this forum and trying many solutions like restart unity or reinstall it. When I type any unity command in terminal like **unity** or **unity --reset-icons**,  it shows some messages indicating that some plugins are starting, but when the message "compiz (core) - Info: starting plugin: ezoom" appears, the system freeze and do not response with nothing.

System freezed after type **unity** command in terminal: 
[http://s2.postimg.org/7sayd2gkp/20160116_155838.jpg](http://s2.postimg.org/7sayd2gkp/20160116_155838.jpg)

Please someone help me! Thanks!

P.S. I do not speak English natively, so sorry if I make any mistake

---

### Post by grahammechanical on 2016-01-16
What theme are you using? Is it either Ambiance or Radiance? Or another theme that you have installed?

Right clicking the background wallpaper should bring up a menu. If we select Change desktop background then System Settings will open at the Appearance utility where we can change the theme.

With System Settings still open you might want to go to Software & Updates>Additional Drivers tab and change the video driver. This is something that I would try.

Regards.

---

### Post by kevin203 on 2016-01-16
Thanks for your reply, unfortunately solution did not work, in Additional Drivers don't appears anything about video drivers. About the theme, before upgrade the system had numix theme, but now after upgrade it have the default theme radiance and I change the theme for ambiance but do not solve the problem. Any other idea?

---

### Post by shaunehunter on 2016-01-23
Today, upgraded to 15.10 from 15.04 and had the same problem.  Unity was removed during the upgrade for some reason.  

I right clicked on the desktop and selected "Open Terminal". Then I launched Synaptic from the terminal by typing "sudo synaptic". In Synaptic I did a search for "unity". Unity was the first programme listed and it's check box was unmarked. I clicked the check box to mark the package and then selected "Apply". Once Synaptic finished installing,  I exited Synaptic using the "File" menu's "Quit" option to stop the program because it was running in the terminal. In the terminal  I then typed the "poweroff" comand. When I started the computer again it was fixed.

I hope this will work for you to.

---

