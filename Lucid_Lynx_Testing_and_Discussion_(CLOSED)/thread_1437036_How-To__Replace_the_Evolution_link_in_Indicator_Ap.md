---
title: "How-To : Replace the Evolution link in Indicator Applet"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by WorldTripping on 2010-03-23
Spent yesterday installing 10.04 and today tinkering.

As I don't use Evolution, preferring Thunderbird, I wanted to find a way to remove the link to Evolution in the Indicator Applet, replacing it with a link to Thunderbird.

Found this, and it works fine.

> 
I am currently working on providing support for the Indicator Applet in my libnotify addon. I already partly figured out how to do it, but the way I’m doing it now it registers a new server for each notification I send. So there’s obviously still a lot of work to do. In the mean time: if you are dying to launch Thunderbird from the Indicator Applet, you can create a file named ‘thunderbird’ in the /usr/share/indicators/messages/applications/ folder with the following contents: ‘/usr/share/applications/thunderbird.desktop’.
That’s it for now, I’ll keep you updated on my work.


From here:

[http://ubublogger.wordpress.com/2009/11/06/indicator-applet-support-thunderbird/]("http://ubublogger.wordpress.com/2009/11/06/indicator-applet-support-thunderbird/")

Hope this helps someone like it helped me today.

Liking Lucid Lynx too. Very fast, not too many useless programs on a first install, tight integration with social networking and IM accounts. Yup I even like the purple wallpaper !

WorldTripping

---

