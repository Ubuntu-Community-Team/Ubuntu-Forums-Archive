---
title: "Can't get Flash working on browers"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by Mung the Wicked on 2008-01-07
Hi.  I want to get flash working on any of my browsers (mainly Firefox and Opera),  I've done this before a few months ago on another Ubuntu machine at work (Feisty), but for the life of me I can't get this to work on my System 76 Serval laptop (Gutsy).  I originally had Gnash to handle the Flash.  The Flash on websites looked like a jumbled mess, as if all the frames were being compacted and displayed all at the same time as a static image.  Bizarre.

Here are the steps that I've taken:
1.) Through Synaptic, I tried installing flashplugin-nonfree.  I then removed it after reading about all the problems with Adobe updating the Flash player and there being problems with it working with Gutsy somewhere in this forum and in other places.

2.) I then went to: [http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore/](http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore/)
and first tried installing the unofficial package with the fix to work with the new version of Flash.  This didn't work  (Oh, the website I've been using to test is Fox Sports with Firefox and then Opera.  For some reason that's the first site that came to mind with Flash other than a bunch of band websites).

3.) So......I tried going to Adobe's site and downloading the .tar file.  I believe this is how I successfully installed Flash the first time on the other computer.  I unzipped the file and ran the installer as root.  I wanted the installation to be system-wide.  I eventually got to a point in the installation where it was asking me for an installation path.  It's example was /usr/lib/mozilla.  I know I had to put in the plugins folder.  So, I typed /usr/lib/mozilla/plugins.  It said it wasn't a valid directory.  The directory is there.  I tried /usr/lib/mozilla/plugins/ and then /usr/lib/mozilla/, and then /usr/lib/mozilla just in case and to be sure.  No dice.

4.) I then tried simply copying with: sudo cp libflashplayer.so /usr/lib/mozilla/plugins.  The file was copied to the appropriate directory.  Firefox was already closed during all this (and the other steps from before).  I restarted it and still nothing.  Now, the Flash just doesn't even show up and Firefox is complaining about the usual missing plugin.

I've tried steps 3-4 with Opera as well and Epiphany, but I get blank spaces where Flash is supposed to be.  Does anyone have an idea?  It's driving me nuts.  I've done this before and this is normally a fairly simple process to get this installed.

Thanks in advance.

---

### Post by xyphur on 2008-01-08
the plugins directory for Firefox isn't /usr/lib/mozilla/plugins/  ...it's actually /usr/lib/firefox/plugins/  (at least that's where I manually copied the libflashplayer.so file from Adobe's .tar file - it worked)

just be sure that the flashplayer-nonfree package isn't installed beforehand, and you shouldn't have any problems....

As for Opera, I don't have any experience with it, but I'd feel safe assuming it's directory and thus plugins directory would be stored in a similar fasion to Firefox's... I'd open up nautilus and poke around /usr/lib/ to see what you can find out, and then repeat the copying of libflashplayer.so in the same manner for Opera.

The only downside to this method is that upgrading Flash should any updates be made to it by Adobe, would also be a manual task... but it doesn't sound like you have any issues working with the CLI, so it's really not that big a deal... besides, how often do they really update it, right? No biggie...

...it's really a matter of ignoring Adobe's default install path in their installer which assumes Mozilla as the installed browser instead of Firefox (which isn't the same thing).

Hope that was helpful!

---

### Post by Mung the Wicked on 2008-01-12
Indeed it was!  Gah, that was the problem.  That's how I installed it in the past - in the firefox directory.  Still trying to get it in Opera, but I will now.  Thanks a bunch!

---

### Post by LeighT on 2008-01-13
Had the same problems trying to indtall Flash plugin, then I followed the advise above and now it works.
Did some investigation and found out that when I installed flash through synaptic, a directory /usr/lib/flashplugins-nonfree was made. But it was empty and nothing was put into the firefox plugins folder.
To add to the confusion synaptic indicated that the plugin was installed.
So I ran apt-get install which returned an error; 
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
So it looks like a between a bug in synaptic and adobe having incorect pathing in their shell script  is confusing every one.
Leigh

---

### Post by Mung the Wicked on 2008-01-13
Yeah, that's a known bug.  I think one of the links I provided in one of my earlier posts directs you to another thread discussing that problem.

---

### Post by zvacet on 2008-01-13
This is how it  works in [Opera](http://www.opera.com/linux/docs/plugins/install/#java).

---

### Post by Mung the Wicked on 2008-01-13
I've already tried the installer from Adobe's site.  When it comes time to tell it an installation path, it tells me /usr/lib/opera/plugins/ is an invalid path even though it exists and I have other plugins in there.  I've also tried installing it manually.  The .so file is in there, and Opera still doesn't play Flash after I reboot it.  I've also made sure that the plug-ins are enabled through Opera's Preferences section on Plug-ins and insured that the correct paths were entered in there as well.  I've no clue why Opera still doesn't work.  This seems like a pretty straight-forward problem to solve.  I've installed the plug-in before albeit was before December and on another Ubuntu machine.

---

### Post by xyphur on 2008-01-13
looking at the page that zvacet posted (scroll up though, his/her link points to the #java anchor on that page, and we're interested in the flash bit), it seems for each bit of information regarding a plugin, they have MIME types at the bottom of each set of instructions. There's got to be a reason for this. I'd check to make sure your Opera's MIME types are setup to use the libflashplayer.so plugin when the browser comes upon swf/flash/shockwave/etc content within pages... without those MIME types setup correctly, it doesn't know what to do with the content, and will likely throw whatever error you're seeing telling you about missing plugins (not sure how Opera handles that sort of situation, if it's anything like Firefox or what, since I've never used Opera myself.)

We'll get this sorted out yet!

---

### Post by xyphur on 2008-01-13
Additionally, to aid in figuring out the MIME settings, this is taken from further up that page:

"General principles of manual installation

The general procedure for manual installation is the following:

   1. Download and install the plug-in
   2. Configure Opera so that it can find the plug-in
   3. Restart Opera

Instructions for the first step are usually given by the plug-in manufacturer, and are repeated below. For the second step, there are at least two alternative procedures: either copy the plug-in to /usr/lib/opera/plugins, where it will be discovered automatically after restarting Opera, or add the directory containing the plug-in to the plug-in path. To add a new directory to the plug-in path, select Tools > Preferences > Advanced > Content, click on "Plug-in options", and "Change path".

After changing the path, restart Opera, and if all went well, the plug-in should be listed under Tools > Advanced > Plug-ins. To be certain that Opera will use the plug-in, and not some alternative application, go to Tools > Preferences > Advanced > Downloads, and select the mime-type associated with the plug-in. Click on "Edit", and make sure that "Use plug-in" is marked appropriately. "

---

### Post by Mung the Wicked on 2008-01-13
> **xyphur said:**
> looking at the page that zvacet posted (scroll up though, his/her link points to the #java anchor on that page, and we're interested in the flash bit), it seems for each bit of information regarding a plugin, they have MIME types at the bottom of each set of instructions. There's got to be a reason for this. I'd check to make sure your Opera's MIME types are setup to use the libflashplayer.so plugin when the browser comes upon swf/flash/shockwave/etc content within pages... without those MIME types setup correctly, it doesn't know what to do with the content, and will likely throw whatever error you're seeing telling you about missing plugins (not sure how Opera handles that sort of situation, if it's anything like Firefox or what, since I've never used Opera myself.)

We'll get this sorted out yet!
Actually, it doesn't throw up an error at all.  It displays a blank box where the Flash should be.  Got another reply coming for your other post.

---

### Post by Mung the Wicked on 2008-01-13
> **xyphur said:**
> Additionally, to aid in figuring out the MIME settings, this is taken from further up that page:

"General principles of manual installation

The general procedure for manual installation is the following:

   1. Download and install the plug-in
   2. Configure Opera so that it can find the plug-in
   3. Restart Opera

Instructions for the first step are usually given by the plug-in manufacturer, and are repeated below. For the second step, there are at least two alternative procedures: either copy the plug-in to /usr/lib/opera/plugins, where it will be discovered automatically after restarting Opera, or add the directory containing the plug-in to the plug-in path. To add a new directory to the plug-in path, select Tools > Preferences > Advanced > Content, click on "Plug-in options", and "Change path".

After changing the path, restart Opera, and if all went well, the plug-in should be listed under Tools > Advanced > Plug-ins. To be certain that Opera will use the plug-in, and not some alternative application, go to Tools > Preferences > Advanced > Downloads, and select the mime-type associated with the plug-in. Click on "Edit", and make sure that "Use plug-in" is marked appropriately. "
Ya, I installed it manually to the correct path and the plug-in path within Opera is set to /usr/lib/opera/plugins as well.  It used to have /usr/lib/mozilla/plugins listed in there as well, but I took that out currently for simplicity's sake.  It didn't work when the mozilla path was listed in there and when it wasn't.

Right now all that's listed in regard to flash plug-ins (in the Plug-ins menu) is:
Shockwave         Shockwave Flash 9.0 r115         /usr/lib/opera/plugins/libflashplayer.so

Now, if I go to Preferences -> Advanced tab -> Downloads I can find the MIME types
application/futuresplash and application/x-shockwave-flash.

If I click on application/futuresplash and the Edit the file extension is set to 'spl' and I have checked "Use plug-in", which lists: Shockwave Flash - /usr/lib/opera/plugins/libflashplayer.so

The same thing applies to application/x-shockwave-flash.

I restarted Opera and nope, and Flash still doesn't work.

---

### Post by zvacet on 2008-01-14
Did you** try tools>preferences<advanced> plug-in options>find new**?

If I remember correctly installer didn´t ask for path (or I yout accepted defaults).Try with installer one more time and now select netscape if Opera is not option for installing.After installing restart Opera and with above command.

---

### Post by Mung the Wicked on 2008-01-14
Well, another good note to all this is that Epiphany and Galeon are running Flash with no problem.

---

### Post by Mung the Wicked on 2008-01-14
> **zvacet said:**
> Did you** try tools>preferences<advanced> plug-in options>find new**?

If I remember correctly installer didn´t ask for path (or I yout accepted defaults).Try with installer one more time and now select netscape if Opera is not option for installing.After installing restart Opera and with above command.
I don't have a netscape or Netscape directory within /usr/lib/

---

### Post by xyphur on 2008-01-14
...this might be the reason why I ended up forgetting about Opera since the first time I tried it back on my windows 98 machine sometime during it's infancy... seems it still hasn't come of age. (I know, I know, flamebait... :D - truth be told, I know a handful of people who swear by it and claim it's a great browser)

I've been using Firefox since pre-1.0 and haven't ever had any reason to try anything else. It just sorta has this tendancy to do everything I tell it or expect it to do. Don't have any reason to bother with anything else...

[/semi off-topic rambling]

I'm glad the other things are working for ya now... :)

---

### Post by Mung the Wicked on 2008-01-14
Nah, don't sweat it Xyphur.  Firefox is indeed a great browser.  It's usually my primary browser, though when I get in certain phases I'll sport Opera for a bit.  The main reason I'm concerned is for Web design purposes and secondly web programming with scripts and whatnots.  Opera behaves slightly different from Firefox and its relatives, so I like to see what CSS/scripts/Java quirks it will toss up.

---

### Post by Mung the Wicked on 2008-01-14
Oh, I forgot to post this in my last post.  I went to Adobe's Flash tester page:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

I then clicked on the area where Flash should have been playing.  I tried this before to instantiate the whole process of "You don't have this plugin, would you like to DL/update it?, etc.", but it wouldn't happen till now on this page.  Anyway, I did just this successfully and I was told the plug-in was not installed and if I would like to download it.  The resulting page told me this:

We are unable to locate a Web player that matches your platform and browser. 

ATTENTION NETSCAPE 6 USERS:

Note: If you have Netscape 6.0, then please update to Netscape 6.1 before installing the Shockwave Player. To determine what version of Netscape you have, select the "About Communicator" option in your browser's Help Menu. Click here to update your browser to Netscape 6.1.

Please visit our table of recommended Web players .


Boooooooooooooo.  I have the plugin manually installed.  It seems like Opera just flat-out doesn't support that plugin?  Hmmmmm.....maybe I'll contact Adobe and see if there's something I could do to get this thing working, though I shudder at the thought of going back and forth with company's support.

---

### Post by zvacet on 2008-01-14
> I don't have a netscape or Netscape directory within /usr/lib/

I mean when you run installer it ask you for wich browser you want to install it an options are mozilla netscape and I don´t kinow if Opera is.Make long story short Opera use natscape plugins and firefox is build on netscape wich make Opera possible to use both plugins.Bacause we work in lunux we accept mozilla plugins and Opera can use it if you decide to work with Opera.I know this is not answer to your question.Only thing I can think of is version of Opera.Do you use 9.5 beta?I think with that version you should not have problem.You can allwasy try on Opera forums.They have subforum for linux.I belive there you will get better and faster answer.Good luck and stay with Opera.

---

### Post by wolfen69 on 2008-01-14
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by zvacet on 2008-01-15
O.K.  maybe I overlooked,but di you installed ubuntu-extras?if you didn´t do it now with 

```
sudo apt-get install ubuntu-restricted-extras
```

That will give you flash,java,plugins...

---

### Post by loopy on 2008-01-16
[>Here is your problem.<]("http://www.opera.com/support/search/view/872/")

... and [>here is your solution.<]("http://fpdownload.macromedia.com/get/flashplayer/current/flash-plugin-9.0.48.0-release.i386.rpm")

(the latest flash plugin (9,0,115,0) isn't supported by Opera 9.2x, so install an older version)

---

### Post by Mung the Wicked on 2008-01-17
> **zvacet said:**
> O.K.  maybe I overlooked,but di you installed ubuntu-extras?if you didn´t do it now with 

```
sudo apt-get install ubuntu-restricted-extras
```

That will give you flash,java,plugins...
I believe I already did that.

---

### Post by Mung the Wicked on 2008-01-17
> **loopy said:**
> [>Here is your problem.<]("http://www.opera.com/support/search/view/872/")

... and [>here is your solution.<]("http://fpdownload.macromedia.com/get/flashplayer/current/flash-plugin-9.0.48.0-release.i386.rpm")

(the latest flash plugin (9,0,115,0) isn't supported by Opera 9.2x, so install an older version)
Loopy, you da' man!  Since post #17 (where I had this line:" We are unable to locate a Web player that matches your platform and browser."), I've been leaning towards that thought.  That confirms it.  I have Opera version 9.25.

I'll install that new version, and post whether it worked or not.  Thanks!

---

### Post by Mung the Wicked on 2008-02-14
Ok.  It worked.  These are the steps I took:
1.) Downloaded and saved the .rpm file you gave me
2.) sudo alien -k flash-plugin-9.0.48.0-release.i386.rpm
3.) dpkg  -i flash-plugin_9.0.48.0-release-1_i386.deb
4.) Opened Opera up, but flash wasn't working.  So I went to:
                               a.) Tools
                               b.) Preferences
                               c.) Advanced
                               d.) Content
                               e.) Plug-in Options
5.) Here, I noticed that the newer, non-compatible flash plug-in was still listed.
6.) So, I took note of its file path, created a new directory within the directory it was located called "plugin-backup" (whatever you want to call it) and copied the compatible flash plug-in (installed via dpkg'ing the .deb file and located in: /usr/lib/flash-plugin/) to the place where the non-compatible flash plug-in once resided (/usr/lib/opera/plugins).
7.) Andddddddd.....................<drum roll>.....................flash in Opera finally worked.  Finally, after all this time.

I would have posted way sooner.  I tried this briefly without doing steps 5-6, but gave up.  Life got extremely crazy (in a good way) at that point in time.  So - I had no time to screw around with this.

Thanks Loopy.  And Thank you zvacet and xyphur.  You guys were a great help!

---

### Post by LeeJay on 2008-02-14
> **Mung the Wicked said:**
> Ok.  It worked.  These are the steps I took:
1.) Downloaded and saved the .rpm file you gave me
2.) sudo alien -k flash-plugin-9.0.48.0-release.i386.rpm
3.) dpkg  -i flash-plugin_9.0.48.0-release-1_i386.deb
4.) Opened Opera up, but flash wasn't working.  So I went to:
                               a.) Tools
                               b.) Preferences
                               c.) Advanced
                               d.) Content
                               e.) Plug-in Options
5.) Here, I noticed that the newer, non-compatible flash plug-in was still listed.
6.) So, I took note of its file path, created a new directory within the directory it was located called "plugin-backup" (whatever you want to call it) and copied the compatible flash plug-in (installed via dpkg'ing the .deb file and located in: /usr/lib/flash-plugin/) to the place where the non-compatible flash plug-in once resided (/usr/lib/opera/plugins).
7.) Andddddddd.....................<drum roll>.....................flash in Opera finally worked.  Finally, after all this time.!

Thank you so, so much! Opera is hands down my favorite browser - it's superfast and has tons of built-in functionality - but the flash problem was driving me nuts! Now it works perfectly! Thanks again!

---

### Post by svantomen on 2008-03-25
Great!

This helped me a lot, especially since I cannot get around the Firefox CPU 100% problem. Now I am all set for Opera

---

