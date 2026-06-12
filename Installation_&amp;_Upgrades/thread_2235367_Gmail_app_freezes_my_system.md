---
title: "Gmail app freezes my system"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by PenguinLust on 2014-07-20
I went to get my Gmail the old fashioned way, and it told me to install an app. So I did, and now whenever I log in, it tells me that it can't connect to my Gmail. So if I go to start the app, it eventually freezes my system, so that even my mouse pointer gets frozen (although, not right way). Also, now when I use Firefox to browse to Gmail, it doesn't load.
I recently got an error about ttf-mscorefonts-installer, so I followed the advice for solution 1 of the best answer at [http://askubuntu.com/questions/153928/failure-to-download-extra-data-files-after-installing-ttf-mscorefonts-installe](http://askubuntu.com/questions/153928/failure-to-download-extra-data-files-after-installing-ttf-mscorefonts-installe). Might that have been the problem?
I'm running Ubuntu 14.04 on an AMD64.

---

### Post by bapoumba on 2014-07-20
What do you call the old fashion way ? A web browser ? Which app did you install ? gnome-gmail or something else ?

---

### Post by PenguinLust on 2014-07-20
Yes: old fashioned == web browser.
I guess it isn't gnome-gmail since running

```
dpkg -l | grep -i gmail
``` didn't indicate anything of the sort, unless you consider unity-webapps-gmail to be something else. If it's alright w/you, I'd rather not start it to try to find out.

---

### Post by tgalati4 on 2014-07-20
There is a Windows gmail app which supposedly will have more functionality than gmail in the web browser.  Over time, google will drop the web client so that you will only be able to access your gmail though the gmail application.  This does not bode well for linux users.  Oh well, as long as they aren't being evil.  Please provide a link where you got this app.  I didn't think it was released yet.

The other possibility is that you downloaded the gmail app for Firefox OS which installs itself into Firefox and can be found in Developer==>App Manager.  This provides an emulation mode for FirefoxOS for those that want to work on phone apps for the new FirefoxOS phone.  Perhaps it is running in the Emulation mode and that locks you out of the webclient.  I don't know I have not messed with FirefoxOS.  Apparently you get an operating system with your "free" browser.

---

### Post by bapoumba on 2014-07-21
Thanks tgalati4, I supposed the OP downloaded the app from the web browser but was not sure.

---

### Post by PenguinLust on 2014-07-21
What I installed wasn't an FF addon, if that's what you mean. I don't quite remember how it went, but I went to Gmail, and some kind of popup (I'm not really used to Gnome) recommended I install a Gmail app. I guess what happened next is I downloaded a Debian package and the software manager installed it, but I don't know. This has happened w/a few of these sites like YouTube and now their icons appear in the "Other" submenu of my applications.

---

### Post by tgalati4 on 2014-07-21
So perhaps these "apps" are real.  Google has a way of rolling things out as an "opt-in" basis.  I was not aware that there would be a linux client.  My understanding is that these "apps" run in html5 and have better performance than running the web client with the browser overhead.  There are several apps in the pipeline.  It's possible that you downloaded a 32-bit version and you are running 64-bit.  It's possible that it doesn't work correctly under Unity.  Who knows?  Without a link for the *.deb, I can't comment or assist.

I have been using gmail for several years, and I tried to search for it on google, and I couldn't find it.  Look in /var/log for log files of recent installations.  If you can get a package name, that would be helpful.

---

### Post by bapoumba on 2014-07-21
Would you please post a screenshot ?

---

### Post by PenguinLust on 2014-07-21
Well, how about this: that naughty app that pooches my system in the menu has this attached to it:
> unity-webapps-runner -n 'R21haWw=' -d 'mail.google.com' --store-session-cookies %u
Does that help?
I think the program which offered the installation just tried to do that w/something else again. I got this popup balloon dropping from the site icon, with the Ubuntu logo on it offering to install some app to make things more efficient and give more features. I'm pretty sure it was something like that that I tried to install which is now causing all these problems.

---

### Post by bapoumba on 2014-07-22
OK thanks, yes that does help, at least me seeing what you were talking about. Not running on unity, I had no real idea.

I think this is a webapp that provides desktop integration : [http://blog.canonical.com/2012/07/19/introducing-ubuntu-web-apps-setting-the-web-free-of-the-browser/](http://blog.canonical.com/2012/07/19/introducing-ubuntu-web-apps-setting-the-web-free-of-the-browser/) ; [https://launchpad.net/webapps](https://launchpad.net/webapps) ; [http://developer.ubuntu.com/apps/](http://developer.ubuntu.com/apps/)

[https://bugs.launchpad.net/ubuntu/+source/webapps-applications/+bug/1068662](https://bugs.launchpad.net/ubuntu/+source/webapps-applications/+bug/1068662) < other bug reports are linked into that one, you may want to read them too.

Do you want to have it work or do you want to remove it ?

From what I have seen, to remove it, just remove the unity-webapps-gmail package, and probably the .desktop file under /home/username/.local/share/applications/<insert_webapp_here>com.desktop : [https://answers.launchpad.net/ubuntu/+source/unity/+question/212703](https://answers.launchpad.net/ubuntu/+source/unity/+question/212703). The example here is for reddit, should work if adapted to gmail.
[https://launchpad.net/ubuntu/+source/unity-webapps-gmail](https://launchpad.net/ubuntu/+source/unity-webapps-gmail)

To have it work, you'll have to try out what has worked for others in the bug report.

---

### Post by PenguinLust on 2014-07-22
Considering the amount of effort above removal that fixing would be, and the limited amount of improvement I would expect from fixing, I think I'll go w/removal.

---

### Post by PenguinLust on 2014-07-30
I removed the offending deb package, so there's no danger of me starting it and freezing. I still some inscrutable popup when I log in telling me that it can't access my Gmail, but I guess that doesn't matter.

---

