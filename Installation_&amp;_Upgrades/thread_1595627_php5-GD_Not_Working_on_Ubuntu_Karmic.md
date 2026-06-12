---
title: "php5-GD Not Working on Ubuntu Karmic"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by adbask on 2010-10-13
Hello everybody,

I have regretted the minute I installed Ubuntu Karmic server version,  well I guess it will be the same even if it's the desktop version:

No Matter what I did the GD library is NOT working, I have it installed with this package

**php5-gd**, but I suspect that some fucntions might be missing and I  don't know who is this smart a** who decided that the bundled version  of the GD would be best for us.

I hate when people don't give you options to choose as if we are kids so  they have to make those ridiculous choices for us, I thought this was a  Microsoft thing, but Ubuntu are doing just the same things bit by bit.

  Is there anyone here please who can tell me or show me how to fix this problem?
I am getting a lot of spam because I can't use the captcha.

Basically some images are not showing on my websites, the paths are correct, permissions are correct.

Yes in the phpinfo() it shows that the gd is installed and enabled with  the support of all the image formats, png, jpeg, gif etc..

especially "CAPTCHA" images, they won't display on my contact forms, if I  use the same files on another server other than karmic it works like a  charme.

**[COLOR=Blue]But not on Karmic, any ideas please? [/COLOR]**

Why do they always have to mess things up, is this what they call progress?

Regards
Ad

---

### Post by paulsp on 2010-10-13
Which PHP version are you using? For me upgrading to 5.3 did the trick.

---

### Post by adbask on 2010-10-13
Hi There,
Thanks for your reply

I am using this version :[SIZE=3] [SIZE=2]PHP Version 5.2.10-2ubuntu6.5

The trouble is, I am sure the minute I use another version, even if it solves the problem of the php5-gd it will most definitely screw something else on my server, I have 3 websites I am sure if I upgrade to php5.3 something will go pear shape.


Besides how did you upgrade to php5.3?

You must've compiled it yourself, am I right?

Which OS ar you using ( I take it Karmic) correct?

I have been using Ubuntu since version 4:10 and to be honest never had this kind of problems until this one.

Any other suggestions please?

Regards
Ad
[/SIZE][/SIZE]

---

