---
title: "So what about default url support any change to see it in final lucid?"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-18
every time i install ubuntu i need to add url support using the fx-url guide i'v found in
one of the forums here is it possible that you add it as default?
 
and how about auto arrange for desktop? keep align option doesn't work so good for
me maybe because i'm using hebrew interface but every time i download files or 
create url shortuts or anything like this the files goes one on top of the other on
the top right corner of the screen and i need to clean by name to fix it. 
 
so maybe an option similier to what ubuntu have in files and folders not on desktop
would be great on desktop.
 
also another option would be the ability to save screenshots in other formats except png 
every time i create shortcuts i need to convert them via gimp in order to reduce there size
so that i could upload them to a software forum i manage that has 300KB upload size limit.
 
i tried nautilis actions there is optipng option there but couldn't get it to work in lucid.
 
i also came upon device manager package that maybe should be added as default.
 
these are things that i think should be basic options in ubuntu 10.04
that is that i can think of at this moment.
 
thanks in advance.

UPDATE:
Some sort of solution for firefox users at least:
[https://addons.mozilla.org/en-US/firefox/addon/66](https://addons.mozilla.org/en-US/firefox/addon/66)

Second solution:
here is a new addon for firefox i arrange that support ubuntu shortcuts  method just to let you know:
[http://rapidshare.com/files/376710629/savelink_v2.0.1.xpi.html](http://rapidshare.com/files/376710629/savelink_v2.0.1.xpi.html)

it would be in the firefox addons web site as save link very soon.

---

### Post by aviramof on 2010-02-18
and also what is going on with Feb 18 developers sprint version where is it?
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

it's already 18:00 on the 18 where i live.

---

### Post by oomingmak on 2010-02-18
> **aviramof said:**
> every time i install ubuntu i need to add url support using the fx-url guide i'v found in one of the forums here is it possible that you add it as default?

Have they still not fixed that yet? 

There was a bug filed about it nearly 2 years ago (and solutions were created and put forward) but it seems that nothing has been done about it since.

[https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165)

---

### Post by aviramof on 2010-02-18
i guess not and it is very annoying that every time that i install ubuntu i need to create fx-url file and etc to fix this problem.

---

### Post by jpeddicord on 2010-02-18
> **aviramof said:**
> every time i install ubuntu i need to add url support using the fx-url guide i'v found in
one of the forums here is it possible that you add it as default?
 
and how about auto arrange for desktop? keep align option doesn't work so good for
me maybe because i'm using hebrew interface but every time i download files or 
create url shortuts or anything like this the files goes one on top of the other on
the top right corner of the screen and i need to clean by name to fix it. 
 
so maybe an option similier to what ubuntu have in files and folders not on desktop
would be great on desktop.
 
also another option would be the ability to save screenshots in other formats except png 
every time i create shortcuts i need to convert them via gimp in order to reduce there size
so that i could upload them to a software forum i manage that has 300KB upload size limit.
 
i tried nautilis actions there is optipng option there but couldn't get it to work in lucid.
 
i also came upon device manager package that maybe should be added as default.
 
these are things that i think should be basic options in ubuntu 10.04
that is that i can think of at this moment.
 
thanks in advance.

Keep in mind that developers typically do not read these forums, so while other community members can see and comment, it may be falling on deaf ears. You may get better results filing ideas on Brainstorm, filing bugs on Launchpad, or going directly upstream to GNOME Bugzilla.

---

### Post by aviramof on 2010-02-18
as oomingmak said this problem is already two years old on Launchpad so what it would do if i post something there now?
 
if any one know a developer here it would be great if someone PM him that is the best
option to fix this problem and no new post on Launchpad would help not in the allotated time for lucid that is.
 
and beside i'm tierd of registering all this sites all the time if people want to fix problems they do it if not they don't.
even if i bother registering to all those site and i post there that doesn't mean they fix it in the end.

---

### Post by aviramof on 2010-02-19
any news?

---

### Post by Jordanwb on 2010-02-19
> **oomingmak said:**
> Have they still not fixed that yet? 

There was a bug filed about it nearly 2 years ago (and solutions were created and put forward) but it seems that nothing has been done about it since.

[https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165)

I have to use mtpfs since gphoto2 doesn't work with my ZEN. I don't have a problem with writing a udev rule but it helps if mtpfs works. A bug was reported with the exact same error two years ago in Hardy Heron. LAst time I saw mtpfs working was in Jaunty. Is it possible to install mtpfs from jaunty and install it in lucid?

</minor_derail>

---

### Post by aviramof on 2010-02-19
is there any developer here who can say he would look into it?

---

### Post by jpeddicord on 2010-02-19
> **aviramof said:**
> is there any developer here who can say he would look into it?

I think you should re-read my last post: developers don't really come by these forums. You will have better luck reporting bugs directly upstream in bugzilla.gnome.org.

---

### Post by aviramof on 2010-02-19
i'm tierd of registering all this sites and nothing happen.
 
if you have an account there you can post it there.
 
thanks in advance.

---

### Post by aviramof on 2010-02-20
ok i posted this:
[https://bugzilla.gnome.org/show_bug.cgi?id=610507](https://bugzilla.gnome.org/show_bug.cgi?id=610507)
 
altoughe i'm sure i did a poor job posting it if there is something you can help me to improve it that would be great.
 
and here is another one:
[https://bugzilla.gnome.org/show_bug.cgi?id=610516](https://bugzilla.gnome.org/show_bug.cgi?id=610516)

---

### Post by aviramof on 2010-02-21
ok it didn't worked so well what can i do now?

---

### Post by 23meg on 2010-02-21
You can do any combination of the following:

[list][*] Try to fix the issue yourself and submit a patch
[*] Convince / pay someone to fix it
[*] Get better at reporting bugs 
[*] Wait[/list]
Keep in mind that using Ubuntu-specific terms such as "Lucid" in bug reports you submit to upstream bug trackers (GNOME in this case, and generally any other component of Ubuntu) will make it harder for developers to understand you, since they may not be familiar with Ubuntu at all. Take a look at [this]("https://help.ubuntu.com/community/ReportingBugs#Writing%20a%20useful%20report") for more tips on making good bug reports.

---

### Post by aviramof on 2010-02-21
as for the wait part there is already a bug report two years old about this problem:
[https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165)
 
how much time should everyone wait for this problem to be solved?
 
but i'll try to make another bug report later maybe it would help.

---

### Post by 23meg on 2010-02-21
[QUOTE=aviramof]as for the wait part there is already a bug report two years old about this problem:
[https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165)

how much time should everyone wait for this problem to be solved?[/QUOTE]

I don't know. I'm neither affected by it, nor interested in working on it. Maybe if you politely contact the people who have shown an interest in fixing it in the bug report, there will be progress.

[QUOTE=aviramof]but i'll try to make another bug report later maybe it would help.[/QUOTE]

No, don't. Not only would it not help; it would hurt. There's no use in filing multiple bug reports on the exact same issue. It only wastes the time of bug triagers who will mark it as a duplicate.

---

### Post by aviramof on 2010-03-13
any news on the matter?i'm tierd of doing it again and again every time i install ubuntu.

---

### Post by aviramof on 2010-03-26
So what about this problem is it possible that we would ever see a permenet solution i'm tierd of doing the guide to add manually ervery time i install ubuntu it's really annoying.

thanks in advance.

---

### Post by aviramof on 2010-04-13
every time i install ubuntu i'm downloading an addon for firefox called save link and then i need to use this somewhat complicated guide to add url support:
[http://ubuntuforums.org/showthread.php?p=3281092](http://ubuntuforums.org/showthread.php?p=3281092)

so is it possible that you would add this support by default? i think that something as ubuntu 10.04 final should at least have this basic option if not auto arrange option on the desktop and some other minor options like the ability to choose main and secondary screen in monitors and all sorts of of options like this.

and i think it would be good if the cd version would have all the applications shortcuts like the dvd version like control panel and gnome-conf and everything you can find in applications other and etc.

[https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165)

---

### Post by aviramof on 2010-04-13
i mean come on how long would it take you to add just one more file type to ubuntu by default or just one more script like the one describe in the guide?

---

### Post by psyke83 on 2010-04-13
> **aviramof said:**
> i mean come on how long would it take you to add just one more file type to ubuntu by default or just one more script like the one describe in the guide?

Do you realize that this is a forum for user testing and discussion, and as a general rule, the developers aren't reading each and every post? Even if a suitable developer who was connected to the mime-type packages (probably "mime-support" or "shared-mime-info") did happen to see your post, they would most likely ignore you. Your complaining is helping nobody, least of all yourself.

If you really want this to happen, file a complete and valid feature request bug on Launchpad (or search to see if one already exists). Read the stickies if you don't know where to start.

---

### Post by aviramof on 2010-04-13
if i'm not mistaken and i'm not there is already a feature request like this more then one and they are more then two years old and nothing happen till now.

[https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165)

maybe if more people here would say it effects them then the developers would fix this problem once and for all.

---

### Post by aviramof on 2010-04-15
if there is already a confirmed bug report about it then why nothing is been done about it?

what more can i do to get this problem fixed once and for all?

---

### Post by aviramof on 2010-04-15
any one?

---

### Post by BrokeMahPC on 2010-04-15
How many people would actually use a feature like this? And why?

---

### Post by ubername on 2010-04-15
> **aviramof said:**
> i mean come on how long would it take you to add just one more file type to ubuntu by default or just one more script like the one describe in the guide?

I think more to the point is how long would it take you?

---

### Post by aviramof on 2010-04-15
> **BrokeMahPC said:**
> How many people would actually use a feature like this? And why?

Why wouldn't people use it when i save a link to a web page via firefox via the extenssion
save link it save it as url and i save it on desktop so i can easily access web sites i often use like threads in this forums for instance.

> **ubername said:**
> I think more to the point is how long would it  take you?
what do you mean how long it take me?

it can take sometime to do the guide and to do it everytime you install ubuntu is very annoying and frustrating why not simply add another default script to the default install and that it once and for all what is so complicated about that?

---

### Post by aviramof on 2010-04-15
and beside the fact that it something that not a lot use it doesn't mean it's not something that need to be fixed for instance like this bug i reported not long ago it's still a bug that need fixing.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)
[http://ubuntuforums.org/showthread.php?t=1432659](http://ubuntuforums.org/showthread.php?t=1432659)

---

### Post by philinux on 2010-04-15
What is the advantage of this url support compared to normal firefox bookmarks?

---

### Post by mcduck on 2010-04-15
...not to mention that Firefox in Linux already has capability of saving web links into desktop shortcuts. Just drag the address from the address bar into your desktop and you'll see. 

The .url file format is only used by Windows, OSX and Linux both have their own formats for this purpose. (.url in windows, .webloc in OSX and .desktop in Linux)

edit: By the way, there's a huge difference between a bug and a feature request... ;)

---

### Post by aviramof on 2010-04-15
ok first of all i have like 1500 bookmarks in Firefox imported from windows and  no matter how much i try to organize them and they are quite organize i would never be able to find the specific link at the right time so i save the newest and most important ones or just the temporary ones on desktop. 

as for the other option i need to to minimize the windows in order to enable to drag from the browser to the desktop but with the addon save link:
[https://addons.mozilla.org/he/firefox/addon/14019](https://addons.mozilla.org/he/firefox/addon/14019)

i can simply right click and then choose save link as file it's similier to IE 
option in windows create shortcut on desktop i'm used to working with this option so i found a solution for it in firefox and i found a solution in ubuntu to enable me to continue using it but to do the guide every time i install ubuntu is not very comftarble.

and i am not the one who reported this bug two years ago:
[https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165)

but never the less it was confirmed but never assign who knows how many more bugs like this still exist today?

---

### Post by Merk42 on 2010-04-15
> **aviramof said:**
> ok first of all i have like 1500 bookmarks in Firefox imported from windows and  no matter how much i try to organize them and they are quite organize i would never be able to find the specific link at the right time so i save the newest and most important ones or just the temporary ones on desktop. 

Unrelated to the bug, but maybe you should use tags to organize those 1,500 bookmarks?

How did you organize **1,500 bookmarks** even in Windows? Did you put them all in organized folders? If so, that's how you can use tags (although even better because you can have the same bookmark with multiple tags)

---

### Post by aviramof on 2010-04-15
yes they are organized in separate folder and i regularly checked them with AM-DeadLink but unrelated to my bookmark i often use this option only for very important links who already have a copy in bookmark or for temporary ones those that i don't need on a permanent basis for instance links to threads i open in this forum and other forums i simply create a shortcut check the threads from time to time and when the threads are no longer in use i simply delete the shortcut it as simple at that and it's very comfortable to work like this sometimes.:)

and by the way the tag option is a really good idea but still it's not practical for temporary shortcuts.

---

### Post by philinux on 2010-04-15
I also have a shed load of bookmarks organised quite well in Firefox and I find the awesomebar search spot on.

---

### Post by Merk42 on 2010-04-15
> **aviramof said:**
> and by the way the tag option is a really good idea but still it's not practical for temporary shortcuts.

Why not? You could tag them TEMP or even just make a more classic Bookmarks Folder called TEMP and put them in there.  When you need to delete them, simply right click -> delete.

---

### Post by aviramof on 2010-04-15
but if i use bookmark i need to first open the browser then go the folder temp or to last tags and etc if i have a link on desktop it immediately open the browser to the page i want that's the beauty of shortcuts on desktop:)

the  awesomebar is also nice as i see now but again it's two or even three actions and not one.:)

---

### Post by BrokeMahPC on 2010-04-15
Well I think me and 99% of others would use Firefox Bookmarks. You say you need this feature because you have 1500 bookmarks? Wow, I think I collect 200 or so every year but end up discarding 75% - have a clear out and tidy up.
It would be entertaining to see you put 1500 url links on your desktop, can we have a picture? :lolflag:

---

### Post by aviramof on 2010-04-15
this is really not the point i need it for the important one and the temporary ones and it's easier and better then use bookmark any way.

and for ubuntu developers it just one more script or even not that just more file extension so why is it so difficult?

---

### Post by aviramof on 2010-04-16
Well to all doubters out there i think it's clear now i'm not the only one who is using this option:
[https://addons.mozilla.org/en-US/firefox/addon/66](https://addons.mozilla.org/en-US/firefox/addon/66)

thank you very much for all your help and i'm still hopping that you add default url support 

so that other browsers could enjoy this option not just firefox.

---

### Post by aviramof on 2010-04-16
here is a new addon for firefox i arrange that support ubuntu shortcuts method just to let you know:
[http://rapidshare.com/files/376710629/savelink_v2.0.1.xpi.html](http://rapidshare.com/files/376710629/savelink_v2.0.1.xpi.html)

it would be in the firefox addons web site as save link very soon.

---

