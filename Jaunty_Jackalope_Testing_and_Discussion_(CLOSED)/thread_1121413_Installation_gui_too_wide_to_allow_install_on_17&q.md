---
title: "Installation gui too wide to allow install on 17&quot; CRT!"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-04-10
I've been doing all of my testing on an LCD 19" Wide screen but just tried to install Jaunty Beta on a friends box with the same hardware other than the monitor which is a 17" CRT.

Once I get as far as the screen where you can import other accounts on a multi-boot I'm stuck! I can scroll up and down thru the import options, but if I hit enter it only "ticks" or "unticks" the selected import option.

Otherwise I'm just stuck there!

Wonderful!

I love the speed, but the bugs are incredible!

It may be good that Jaunty is named after a fictional animal because this is beginning to look like a fictional release!

---

### Post by taavikko on 2009-04-10
I didn't have any problems installing on 8.9" (1024*600)

Did it recognize the monitor correctly?

You can drag the windows if they're not fitting the screen with Alt+Mouse1.
But yet again, it's still beta and freezed so dev's can work out the remaining issues. 

Have you checked that there's correspondent bugs in "ubiquity" ?
Otherwise it may never get resolved...

---

### Post by kansasnoob on 2009-04-10
Sorry for the "snark" at the end of my comments. I was tired and a bit angry.

Alt > Left mouse key won't move these windows in ubuiquity. I tried again this morning.

A few things I need to check:

Is the version of ubiquity on the Beta Live CD the same as the current version of ubiquity?

I'll also try the Alpha 6 Live CD that I have and see if works.

I did find a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/325958](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/325958)

Where it says: "I can confirm it now works fine on 800x480 with the latest UNR nightly image. I see your point about horizontal space though." (2009-04-07)

So, if the current version of ubiquity is different than that on the Beta disc I'll DL and burn the new daily build.

Basically I'll gather more info and then either file a new bug report or add comments to the existing bug report.

After lunch ;)

BTW, I got the friends computer going by using my monitor and now I'm using an old spare 17" CRT just to do testing.

---

### Post by taavikko on 2009-04-10
Whops, my bad, I used alternate-installer when installing on that 8,9" (aspireone)

As for further tinkering, I don't think it's entirely ubiquity's fault, some kind of X/gtk error when not recognizing monitor capabilities and not scaling to correct size the window.

---

