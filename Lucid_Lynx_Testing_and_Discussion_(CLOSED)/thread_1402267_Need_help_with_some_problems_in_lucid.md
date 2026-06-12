---
title: "Need help with some problems in lucid"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-08
here is a list of the problem i have already endounter

1.startup manager give me this error:
```
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```and also he longer appear in system preference and in fact i have another problem with that when i first inslled it i installed it in hebrew and a large part of the things there were in hebrew and then later it's as if 
the menu reset itself now everything is in english and the startup manager don't exist there anymore and
in fact i don't think he works at all i set windows 7 to be default and it didn't worked maybe because i'm 
using grub 2 now and i need grub 2 startup manager.

2.there is no alt shift option to replace langguges 

3.when i try dual view via system-preference-display i see my computer there but the screen is pink and when i shut down my computer the screen turn green with ubuntu in the middle and also the computer don't shut down i have to do it manually.

4.the clock is out of tune in like two hours time here at the moment is 06:44am the clock show 08:44 and i can't change it i set the weather at least to tel aviv israel

5.the spell check in this forum marks every word i write in red line which did not happen before and by the way why is there ask.com is firefox search and not google?

6.and here is another strange thing the clock display 08:53 but when i edit it said "*[Last  edited by aviramof]("http://ubuntuforums.org/posthistory.php?p=8797682"); 1 Minute Ago at 06:5 AM..                                                            "* so the os time is right just the display is not.

that is all for now and thanks in advance.

OH AND LAST THING IF YOUR ALREADY DEVELOPING IS IT POSSIBLE TO ADD AUTO ARRANGE OPTION FOR INSTANCE IN DESKTOP EVERY TIME I DOWNLOAD SOMETHING THE FILES GO THE THE SAME PLACE ONE ON TOP OF THE OTHER AND I WOULD LIKE TO SEE IT FIX

---

### Post by phenest on 2010-02-09
We're not developers. You need to report these as bugs on Launchpad.

---

### Post by aviramof on 2010-02-09
ok.

and by the way why doesn't gimp come as a default software here?

---

### Post by [h2o] on 2010-02-09
> **aviramof said:**
> ok.

and by the way why doesn't gimp come as a default software here?

Because it is has been decided that Ubuntu can make do with a simpler photo editor/organizer instead. Users who need a photo manipulation program of Gimp's strength can download it as usual.
There are already a few threads about this and a mailing list post which in more detail describes this action. I am saying this to not make this thread into an unnecessary "why was Gimp removed" thread.

---

### Post by ranch hand on 2010-02-09
> **'[h2o] said:**
> Because it is has been decided that Ubuntu can make do with a simpler photo editor/organizer instead. Users who need a photo manipulation program of Gimp's strength can download it as usual.
There are already a few threads about this and a mailing list post which in more detail describes this action. I am saying this to not make this thread into an unnecessary "why was Gimp removed" thread.

[http://ubuntuforums.org/showthread.php?t=1330937](http://ubuntuforums.org/showthread.php?t=1330937)

83 pages and counting.

---

### Post by aviramof on 2010-02-09
well you can count me in this one of this 83 pages one of the things i liked in ubuntu is gimp i despise windows 7 painter and all there other minimal basic software what most got me to search for replacment 
is there rdp not heaving simultanius connection or more commenly know view mode you view someone 
can move the mouse but no microsoft decided that this option only belong to windows servers something
that even free softwares like teamviewr provide.

and basicly they don't have a single software that i like there all bad and i have to find 3rd softwares to download at least here it's a lot easier to find and download software then in windows 7.

and here you can't even move your files and orgenize them like you want here you don't even have an auto arrange option altoughe i would like to see a basic auto arrange option in ubuntu.

---

### Post by OrangeCrate on 2010-02-09
> **'[h2o] said:**
> Because it is has been decided that Ubuntu can make do with a simpler photo editor/organizer instead. Users who need a photo manipulation program of Gimp's strength can download it as usual.
There are already a few threads about this and a mailing list post which in more detail describes this action. **I am saying this to not make this thread into an unnecessary "why was Gimp removed" thread.**

Agreed. I have never been able to understand the venomous reaction some have when their pet program is dropped from a default install. Particularly, when "apt-get install <whatever>" rights their world so quickly.

---

### Post by kansasnoob on 2010-02-09
Well, aside from Gimp no longer being installed by default my answer is mostly, "I don't know", except for this:

> 1.startup manager give me this error:

```
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
```

and also he longer appear in system preference and in fact i have another problem with that when i first inslled it i installed it in hebrew and a large part of the things there were in hebrew and then later it's as if
the menu reset itself now everything is in english and the startup manager don't exist there anymore and
in fact i don't think he works at all i set windows 7 to be default and it didn't worked maybe because i'm
using grub 2 now and i need grub 2 startup manager.

Startup Manager has nothing to do with the internet so it makes no sense. Do you mean Network Manager?

I suspect largely a language pack problem but it's impossible for me to troubleshoot because I only know English.

I hope you can find an answer. I'd like to think that Ubuntu supports all languages.

---

### Post by Reiger on 2010-02-09
[list="1"]
[*]Looking at the error message it seems to want to tell me (you) that something between gdm & gconf is broken. You can from a commandline (Ctrl + Alt + F1 thru F9 or so) log in (user name and password as per your account), and then use apt-get or aptitude to (re) install packages or fix broken ones.

May I ask: did you use a partial upgrade to break your system like that? (I do not run Gnome/GDM/Gconf; I use KDE so I am spared this particular scenario.)
[*]I do not know what the heck this is. But as it seems you are using some kind of Gnome that is also heavily broken when it comes to preferences/settings/configuration (that is the job of gconf, which is broken on your system, see?) ... There is some thoughts I can offer you:
-a Gnome is in a bit of transitioning phase, as is Ubuntu. It is supposedly a tidying-up act as I understand it, things are in flux and may not be there or where you expect them to be right now.
-b Gnome depends so heavily on Gconf that is not worth bothering with anything much until you get that working (again)
[*]Funky plymouth. Yeah I have that on my laptop where I forcibly disabled KernelModeSetting on boot: the screen will be a green flicker before the log in screen comes up. I, myself, cannot use KMS because there is a KMS problem that will cause the X server to die slowly and painfully when just after I log in. Use radeon.modeset=0 or nomodeset to disable KMS on boot.

As for your second screen, why it should not be used properly and remain pink I have no idea. Still, fix gconf first; dual-head/Xinerama/w-ever second I would say.
[*]Time zone data is messed up. I presume it is reading system clock UTC data and does not convert it to your local timezone? This, again, depends on gconf I think -- it stores your time zone preference.
[*]You are confusing times displayed by this forum with time displayed by your own machine. The time stamps (Last edited etc.) you see on this forum are tracked, maintained, and converted by the forum software which sits atop a completely different machine from your own (namely the forums' webserver). They are just HTML to your machine, a bit of text. Not a time stamp.

These forum timestamps are not affected by your gconf trouble because firstly the settings of your forum account are not stored on your own machine/gconf but in the forums' database and secondly because these stamps can (a) be generated from UTC stamps (standard time, not yet converted to local time), and (b) those UTC stamps need not come from your own machine when you post something -- they might very well be stamps that are automatically generated by the forums' webserver when it receives your post/edit.
[/list]

---

### Post by aviramof on 2010-02-09
thank you very much for your help and i'm hopping that updates over time would slowly solve all this problems and other that i constaly come accross with.
 
and maybe i did downloaded partial updates before but since then i already formated and installed a clean version and i have no intention of downloading partial updates any more.

---

### Post by cariboo on 2010-02-09
First off, do use all caps in your posts, it is very impolite.

From your comments, your installation is severely broken. Downloaded files now go in a Default Download directory, the directory is created on install.

The ask.com search is also not a part of the default installation, Yahoo will become the default search site when Lucid is released.

I would suggest instead of waiting for updates to fix your problems, do a clean install, and make sure the installation finishes, this should solve several of your problems.

---

### Post by aviramof on 2010-02-09
i do have a very clean install any way i'v used recovery mode fix broken pacages option and downloaded updates so now everything is working better.

i guess i simply should not download too many pacages for the time being before new versions would be released and that it.

---

