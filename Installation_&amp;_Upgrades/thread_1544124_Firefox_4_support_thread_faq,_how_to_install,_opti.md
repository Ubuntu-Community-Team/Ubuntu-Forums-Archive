---
title: "Firefox 4 support thread: faq, how to install, optimize, customize..."
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by lovinglinux on 2010-08-02
See the new [Firefox 4 Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by fremantle on 2010-08-02
cool

---

### Post by fremantle on 2010-08-02
i kinda hav an issue.. i installed the pre beta version and the name shows as "Mozilla Developer Preview", which is version 4.0b3pre. BUT, now i have a DIFFERENT browser, codename namaroka, which is ff 3.7 beta o_O im totally confused

---

### Post by lovinglinux on 2010-08-03
> **fremantle said:**
> i kinda hav an issue.. i installed the pre beta version and the name shows as "Mozilla Developer Preview", which is version 4.0b3pre. BUT, now i have a DIFFERENT browser, codename namaroka, which is ff 3.7 beta o_O im totally confused

First of all, please remove the contents of your first post. They are wrong and have already been covered properly in my instructions.

You should not add all those ppa repositories simultaneously. There is no purpose on that, since they are for the same packages. Additionally, read the important notes about PPA in my first post. The PPA will also update your default Firefox. That's why you have Namoroka now. Remove those PPA repositories and reinstall firefox.

```
sudo apt-get install --reinstall firefox
```

Assuming you have Firefox 4 on the opt folder, that you have downloaded form Mozilla, do this:

```
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox
```

That is the correct way of doing it.

You can start Firefox 4 with the command **firefox** or you can create a launcher pointing to /opt/firefox/firefox

Don't add the ppa again. As stated in my first post, you should use one method or the other.

---

### Post by lovinglinux on 2010-08-03
I have updated the first post with lots of new stuff.

---

### Post by lovinglinux on 2010-08-05
Firefox 4 Beta 3 is about to be released. It was scheduled for today, but according to [Mozilla Wik]("https://wiki.mozilla.org/Releases")i updates, it will be released on Monday or Tuesday. Nevertheless, extensions developers already received the green light to change extensions compatibility to match versions 4.0b3 and 4.0b4pre.

I'm already running the second candidate build of 4.0b3. So far is looking really great, although the very anticipated new UI is still not available for Linux, as well as the revolutionizing [TabCandy]("http://ubuntuforums.org/showthread.php?t=1542777") feature.

Firefox 4 is currently exhibiting more than 200% increase in performance, compared to 3.0.19. The performance boost, when compared to it's predecessor, is even bigger than when Firefox 3.5 was released. See benchmarks below (higher is better).

[IMG]http://tinyurl.com/258nxxw[/IMG]

---

### Post by Pogeymanz on 2010-08-06
In your screenshots, do you have the menubar disabled? I'm still running Beta2 (and the Beta4 nightly, which doesn't work for me yet). And I can't uncheck the menubar.

---

### Post by lovinglinux on 2010-08-06
> **Pogeymanz said:**
> In your screenshots, do you have the menubar disabled? I'm still running Beta2 (and the Beta4 nightly, which doesn't work for me yet). And I can't uncheck the menubar.

Yes I have. I was able to disable it once, but now that you asked, I tried again and I couldn't, even on a new profile.

---

### Post by Pogeymanz on 2010-08-07
Well that's a shame. Firefox is so close to how I want it to look now that I have compact menu 2.

EDIT: Also, that SQLite Optimizer addon you suggested -is it any different/better than your firefox-optimize script?

---

### Post by lovinglinux on 2010-08-07
> **Pogeymanz said:**
> Well that's a shame. Firefox is so close to how I want it to look now that I have compact menu 2.

Don't worry, I'm sure it will be fixed soon.

> **Pogeymanz said:**
> EDIT: Also, that SQLite Optimizer addon you suggested -is it any different/better than your firefox-optimize script?

Not really. Is just more convenient.

---

### Post by lovinglinux on 2010-08-07
Help to shape the next beta by suggesting and voting for new features and improvements at [https://firefox.uservoice.com/forums/57440-firefox-4-beta](https://firefox.uservoice.com/forums/57440-firefox-4-beta)

[IMG]http://tinyurl.com/2eejx7e[/IMG]

---

### Post by lovinglinux on 2010-08-07
I have created some feature suggestions. Please vote for them:

[LIST]
[*][Add extension benchmarks to the add-ons manager]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/970915-add-extension-benchmarks-to-the-add-ons-manager")
[*][Add an option to optimize sqlite databases manually and on exit]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/970903-add-an-option-to-optimize-sqlite-databases-manuall")
[*][Add context menu editor with nesting entries]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/970921-add-context-menu-editor-with-nesting-entries")
[*][Include TabCandy in the final release]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/970955-include-tabcandy-in-the-final-release")
[/LIST]

---

### Post by lovinglinux on 2010-08-09
A new version of Organize Search Engines, already compatible with Firefox 4.0b4pre, has been released. Nevertheless, it hasn't been reviewed by Mozilla yet, so you need to download it manually from [https://addons.mozilla.org/en-US/firefox/addon/4565/versions/](https://addons.mozilla.org/en-US/firefox/addon/4565/versions/)

---

### Post by lovinglinux on 2010-08-09
A new version of Stylish, which is compatible with Firefox 4.0b2 has been released.

---

### Post by SilverWave on 2010-08-10
> **lovinglinux said:**
> Firefox 4 Beta 3 is about to be released...** although the very anticipated new UI is still not available for Linux, **
hmm this is annoying.

---

### Post by lovinglinux on 2010-08-10
> **SilverWave said:**
> hmm this is annoying.

Indeed. Nevertheless, I'm more excited about TabCandy than the new UI.

---

### Post by SilverWave on 2010-08-11
> **lovinglinux said:**
> Indeed. Nevertheless, I'm more excited about TabCandy than the new UI.
hmm I have used "Tree Style Tabs" (show a stacked list of grouped tabs at the left) for a while now... so not sure if I will need TabCandy, Nice idea through.

---

### Post by SilverWave on 2010-08-11
> **lovinglinux said:**
> I have created some feature suggestions. Please vote for them:

[LIST]
[*][Add extension benchmarks to the add-ons manager]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/970915-add-extension-benchmarks-to-the-add-ons-manager")
[*][Add an option to optimize sqlite databases manually and on exit]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/970903-add-an-option-to-optimize-sqlite-databases-manuall")
[*][Add context menu editor with nesting entries]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/970921-add-context-menu-editor-with-nesting-entries")
[*][Include TabCandy in the final release]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/970955-include-tabcandy-in-the-final-release")
[/LIST]


Here are my votes:

[LIST=1]
[*]          [B][3 votes > Vertical Tabs (as an option)]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/889001-vertical-tabs-as-an-option-") 
[/B]
[*]**       [3 votes > New tab homepage]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/888159-new-tab-homepage")**
[*]**[3 votes > The Linux version should have all of the interface enhancements of the Windows Version]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/888243-the-linux-version-should-have-all-of-the-interface")**
[*]**[1 vote >   Speed up Firefox startup !!!]("https://firefox.uservoice.com/forums/57440-firefox-4-beta/suggestions/890849-speed-up-firefox-startup-")             **
[/LIST]

---

### Post by lovinglinux on 2010-08-11
Firefox Beta 3 is officially available for download from Mozilla site folks.

[http://www.mozilla.com/en-US/firefox/beta/](http://www.mozilla.com/en-US/firefox/beta/)

---

### Post by lovinglinux on 2010-08-13
TabCandy is coming! Wooohoo!

> **SilverWave said:**
> [Mozilla bolting Tab Candy on to Firefox 4 today]("http://www.downloadsquad.com/2010/08/12/tab-candy-firefox-4/")

I wonder if I will end up using this...

I am happy with Tree Style Tabs... but this looks cool and it is built-in... hmmm.

---

### Post by lovinglinux on 2010-08-13
Adblock Plus is not working well with Firefox 4.0b4pre from the nightly builds. For instance, I wasn't able to open any Google services.

---

### Post by Helkaluin on 2010-08-13
> **lovinglinux said:**
> *Will TraceMonkey be enabled on 64bit too?*
[LIST]
[*]Although Mozilla doesn't release an official 64bit version and TraceMonkey was disabled on Firefox 3.6 64bit, looks like it will be supported by default now.
[/LIST]
Right, I just want to confirm something: so even if I have <javascript.options.jit.chrome> and <javascript.options.jit.content> enabled in the 64-bit build, TraceMonkey is not enabled? (This being the 3.6.x build found in the official Ubuntu repo.)

I read in <https://wiki.mozilla.org/JavaScript:TraceMonkey> that TraceMonkey is available in the nightly builds for 64-bit. Does the ubuntu-mozilla-daily repo include that? Or do I have to grab the nightlies via ftp?

Aslo, from here: <http://blog.mozilla.com/rob-sayre/2010/08/02/mozillas-new-javascript-value-representation/> there's mention of JaegerMonkey. Is it still TraceMonkey being bundled in the betas now?

---

### Post by lovinglinux on 2010-08-14
> **Helkaluin said:**
> Right, I just want to confirm something: so even if I have <javascript.options.jit.chrome> and <javascript.options.jit.content> enabled in the 64-bit build, TraceMonkey is not enabled? (This being the 3.6.x build found in the official Ubuntu repo.)

Yes. Those preferences are set as enabled by default, but they don't make any difference.

> **Helkaluin said:**
> 
I read in <https://wiki.mozilla.org/JavaScript:TraceMonkey> that TraceMonkey is available in the nightly builds for 64-bit. Does the ubuntu-mozilla-daily repo include that? Or do I have to grab the nightlies via ftp?

No, as far I know ubuntu-mozilla-daily does not include it for FF 3.6 64bit series. It was available in the **trancemonkey** nightly builds, but they are not maintained anymore and hasn't been well tested.

> **Helkaluin said:**
> Aslo, from here: <http://blog.mozilla.com/rob-sayre/2010/08/02/mozillas-new-javascript-value-representation/> there's mention of JaegerMonkey. Is it still TraceMonkey being bundled in the betas now?

I'm not sure if JaegerMonkey completely replaces TraceMonkey or is just an upgrade of the current engine. Nevertheless, it is supposed to be shipped with Firefox 4. To avoid confusion, let's say Firefox 4 jit options will be effective on 64bit. The latest mozilla-central builds already have it and ubuntu-mozilla-daily should have it too.

---

### Post by ubudog on 2010-08-14
Nice thread!  Thanks for posting.

---

### Post by lovinglinux on 2010-08-14
> **ubudog said:**
> Nice thread!  Thanks for posting.

Thanks. You are welcome.

---

### Post by Helkaluin on 2010-08-15
> **lovinglinux said:**
> I'm not sure if JaegerMonkey completely replaces TraceMonkey or is just an upgrade of the current engine. Nevertheless, it is supposed to be shipped with Firefox 4. To avoid confusion, let's say Firefox 4 jit options will be effective on 64bit. The latest mozilla-central builds already have it and ubuntu-mozilla-daily should have it too.
Ah. Many thanks. I was reluctant to test Firefox 4 because vimperator didn't work at all - but the latest snapshot worked (when forced), and good lord Firefox 4 does feel snappier than 3.6.x

---

### Post by lovinglinux on 2010-08-15
> **Helkaluin said:**
> Ah. Many thanks. I was reluctant to test Firefox 4 because vimperator didn't work at all - but the latest snapshot worked (when forced), and good lord Firefox 4 does feel snappier than 3.6.x

You can also test your version by disabling jit in the preferences and the benchmarking it with [Peacekeeper]("http://service.futuremark.com/peacekeeper/index.action"). Then perform the benchmark again, but this time with jit enabled. You will see a noticeable difference in the results.

---

### Post by lovinglinux on 2010-08-15
I have made a video showing TabCandy, SpeedDial, TabScope and Tree Style Tab in action together.

[http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-tab-show.html](http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-tab-show.html)

---

### Post by rollin on 2010-08-15
> **lovinglinux said:**
> I have made a video showing TabCandy, SpeedDial, TabScope and Tree Style Tab in action together.

[http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-tab-show.html](http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-tab-show.html)

Cool video and blog. Thanks!

---

### Post by lovinglinux on 2010-08-16
> **rollin said:**
> Cool video and blog. Thanks!

Thanks.

---

### Post by lovinglinux on 2010-08-17
[Firefox 4.0b4]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/4.0b4-candidates/") **candidates** are available, with TabCandy. Nevertheless, Tree Style Tab and AdblockPlus doesn't work with it.

---

### Post by ubudog on 2010-08-17
> **lovinglinux said:**
> [Firefox 4.0b4]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/4.0b4-candidates/") **candidates** are available, with TabCandy. Nevertheless, Tree Style Tab and AdblockPlus doesn't work with it.

Cool.

---

### Post by lovinglinux on 2010-08-17
> **ubudog said:**
> Cool.

Keep in mind this is not the final beta yet, just a candidate.

---

### Post by ubudog on 2010-08-17
> **lovinglinux said:**
> Keep in mind this is not the final beta yet, just a candidate.

Yes.  But still cool.

---

### Post by lovinglinux on 2010-08-18
> **ubudog said:**
> Yes.  But still cool.

Yep, indeed. The final beta should be available on Monday.

I'm currently using Beta 3 because Beta 4 is messing with Tree Style Tab extension :(. Nevertheless, Beta 4 is a great opportunity to get acquainted with TabCandy. BTW, I have noticed that TabCandy button is not added to the toolbar by default on Beta 4, so you need to right-click the toolbar, select customize and drag TabCandy button to the toolbar.

BTW, AdblockPlus already released a compatible version.

---

### Post by Irony on 2010-08-18
I can't see an obvious way of installing 64 bit Firefox - with Chrome or Opera I just download the 64 bit debs.

Is there a 64 bit tar.gz of Firefox and if so where is it?

---

### Post by lovinglinux on 2010-08-18
> **Irony said:**
> I can't see an obvious way of installing 64 bit Firefox - with Chrome or Opera I just download the 64 bit debs.

Is there a 64 bit tar.gz of Firefox and if so where is it?

You need to get it from the nightly repository, since Mozilla doesn't release a 64bit official build.

**Latest nightly FF4: **

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/)

or [http://nightly.mozilla.org](http://nightly.mozilla.org)

**Latest nightly FF 3.6.x:**

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.2/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.2/)

---

### Post by Irony on 2010-08-18
Thanks for that - it seems odd that Firefox is a major browser without official 64 bit support, I wonder if this is reflection of their losing ground to the likes of Chrome and even Opera.

---

### Post by lovinglinux on 2010-08-18
> **Irony said:**
> I wonder if this is reflection of their losing ground to the likes of Chrome and even Opera.

I don't think so. It has been like this always. The competition is only making Mozilla improve the javascript engine to catch up with the benchmark bandwagon, implement new features like plugin process isolation and redesign the UI to be chromeless (more content space and less graphical interface). Firefox 4 covers all that and a lot more.

---

### Post by Irony on 2010-08-18
Sure... but how can Firefox miss something as basic as 64 bit support, its like building a new model of car with only token support for motorway driving, as though motorways don't really exist.

---

### Post by ubudog on 2010-08-18
> **Irony said:**
> Sure... but how can Firefox miss something as basic as 64 bit support, its like building a new model of car with only token support for motorway driving, as though motorways don't really exist.

Remember it's still beta.

---

### Post by lovinglinux on 2010-08-18
> **Irony said:**
> Sure... but how can Firefox miss something as basic as 64 bit support, its like building a new model of car with only token support for motorway driving, as though motorways don't really exist.

Not really, because is not like Adobe for example that don't release a Flash 64bit version at all anymore. Mozilla build 64bit binaries for every new Firefox version and make them available through the ftp site and if you have Ubuntu 64bit you are using it. The only thing is that they don't release it officially as a final product that you can download when you visit [http://www.mozilla.com/en-US/firefox/upgrade.html](http://www.mozilla.com/en-US/firefox/upgrade.html).

---

### Post by lovinglinux on 2010-08-19
Some interesting data about add-ons:

Of the 790 add-ons that make up 95% of add-on usage known to Mozilla, 11% are currently considered compatible with the latest builds of Firefox 4.0. Nevertheless, only 37% is not compatible with any version of Firefox 4.

The list and compatibility of these 790 add-ons, that are the most popular, can be found at [https://addons.mozilla.org/en-US/firefox/compatibility/report](https://addons.mozilla.org/en-US/firefox/compatibility/report)

[https://addons.mozilla.org/en-US/firefox/compatibility/](https://addons.mozilla.org/en-US/firefox/compatibility/)

[IMG]http://tinyurl.com/26mp3mm[/IMG]

---

### Post by BigCityCat on 2010-08-19
Thanks lovinglinux, it's good to know adblock and noscript are working now. Any word on the new ui for Linux yet.

---

### Post by lovinglinux on 2010-08-19
> **BigCityCat said:**
> Thanks lovinglinux, it's good to know adblock and noscript are working now. Any word on the new ui for Linux yet.

Nope. But TagCandy is coming on the next beta :)

---

### Post by ubudog on 2010-08-19
> **lovinglinux said:**
> Nope. But TagCandy is coming on the next beta :)

Can't wait! :p

---

### Post by lovinglinux on 2010-08-19
> **ubudog said:**
> Can't wait! :p

Should be released on Monday.

My extensions are already compatible with 4.0b4 and 4.0b5pre. Received the green light yesterday, so is coming...

---

### Post by ubudog on 2010-08-19
> **lovinglinux said:**
> Should be released on Monday.

My extensions are already compatible with 4.0b4 and 4.0b5pre. Received the green light yesterday, so is coming...

Ok.  Cool.

---

### Post by lovinglinux on 2010-08-24
Firefox Beta 4 is out. Is not available from the Beta page yet, but you can get it from Mozilla FTP site:

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b4/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b4/)

---

### Post by lovinglinux on 2010-08-24
**Firefox Beta 4 officially released:**

[http://blog.mozilla.com/blog/2010/08/24/firefox-4-beta-updated-with-sync-and-panorama/](http://blog.mozilla.com/blog/2010/08/24/firefox-4-beta-updated-with-sync-and-panorama/)

**Download:**

[http://www.mozilla.com/en-US/firefox/beta/](http://www.mozilla.com/en-US/firefox/beta/)

**Features: **

[http://www.mozilla.com/en-US/firefox/beta/features/](http://www.mozilla.com/en-US/firefox/beta/features/)

---

### Post by lovinglinux on 2010-08-27
I have changed my Firefox 4 interface and workflow again. This time, I'm using a tabless setup.

Video, how-to and explanation available in[ my blog]("http://lovinglinuxblog.blogspot.com/2010/08/firefox-4-customization-tabless.html").

[IMG]http://tinyurl.com/232oe6j[/IMG]

---

### Post by ubudog on 2010-08-27
Looks nice.

---

### Post by Helkaluin on 2010-08-31
Looks like JM and TM are finally merged. See: <arewefastyet.com>

---

### Post by lovinglinux on 2010-08-31
> **Helkaluin said:**
> Looks like JM and TM are finally merged. See: <arewefastyet.com>

Indeed. Thanks for sharing.

---

### Post by lovinglinux on 2010-09-01
EDIT: nevermind

---

### Post by lovinglinux on 2010-09-01
Beta 5 is about to be released. The first candidate is available [here]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/4.0b5-candidates/build1/"). 

It breaks these extensions I have tested so far ](*,)

[LIST]
[*]Secure Login
[/LIST]

---

### Post by ron999 on 2010-09-02
Hi
I have tried the beta 4 Firefox.
That 'Panorama' is very impressive.:p
However, it plays havoc with the Classic Compact theme that I use.:(
So I've preferred to use beta 3.
Today I compiled an optimized Firefox-4.0b3 using the method shown on LovingLinux blog.:guitar:
Here:-[http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lovinglinuxtut+%28lovinglinuxtut%29]("http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lovinglinuxtut+%28lovinglinuxtut%29")

This method is good.:p

There were several compilation errors.
When I used the **--with-system-libxul** configure argument it cured them.

The last commands of the tutorial are:-
```
make
```
and
```
sudo checkinstall 
```

This does a good job. It installs Firefox properly and creates a deb file to use again.

My question is this.
How do I make a 'tarball' like the ones that are available from mozilla?
(Sometimes I would prefer not to install a new firefox till I've run it from a temporary folder).

---

### Post by lovinglinux on 2010-09-02
> **ron999 said:**
> Hi
I have tried the beta 4 Firefox.
That 'Panorama' is very impressive.:p
However, it plays havoc with the Classic Compact theme that I use.:(
So I've preferred to use beta 3.
Today I compiled an optimized Firefox-4.0b3 using the method shown on LovingLinux blog.:guitar:
Here:-[http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lovinglinuxtut+%28lovinglinuxtut%29]("http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lovinglinuxtut+%28lovinglinuxtut%29")

This method is good.:p

There were several compilation errors.
When I used the **--with-system-libxul** configure argument it cured them.

The last commands of the tutorial are:-
```
make
```
and
```
sudo checkinstall 
```

This does a good job. It installs Firefox properly and creates a deb file to use again.

My question is this.
How do I make a 'tarball' like the ones that are available from mozilla?
(Sometimes I would prefer not to install a new firefox till I've run it from a temporary folder).

It seems you can convert a deb to tar.gz with Alien. Never tried tho.

---

### Post by Helkaluin on 2010-09-02
```
make package
``` in the object directory?

---

### Post by ron999 on 2010-09-02
> **lovinglinux said:**
> It seems you can convert a deb to tar.gz with Alien. Never tried tho.
Hi
Yes, alien will do this.
```
alein -t foo.deb
```

It doesn't produce a package like the ones from mozilla though.

---

### Post by ubudog on 2010-09-02
Anyone know when the full version will be released?  Can't wait.

---

### Post by lovinglinux on 2010-09-02
> **ron999 said:**
> Hi
Yes, alien will do this.
```
alein -t foo.deb
```

It doesn't produce a package like the ones from mozilla though.

See Helkaluin suggestion.

> **ubudog said:**
> Anyone know when the full version will be released?  Can't wait.

Probably November. Beta 5 should be available on September 7th. We can expect at least two more betas after that. The Release Candidate 1 is scheduled for the second half of October.

---

### Post by ron999 on 2010-09-02
> **lovinglinux said:**
> See Helkaluin suggestion.




What's that supposed to mean?

---

### Post by lovinglinux on 2010-09-02
> **ron999 said:**
> What's that supposed to mean?

[http://ubuntuforums.org/showpost.php?p=9797529&postcount=59](http://ubuntuforums.org/showpost.php?p=9797529&postcount=59)

---

### Post by ron999 on 2010-09-02
> **lovinglinux said:**
> [http://ubuntuforums.org/showpost.php?p=9797529&postcount=59](http://ubuntuforums.org/showpost.php?p=9797529&postcount=59)

Forget it man, I'll ask the question somewhere else.

---

### Post by lovinglinux on 2010-09-03
> **ron999 said:**
> Forget it man, I'll ask the question somewhere else.

I don't understand what is going on. Helkaluin suggested to cd into the object directory and then run:

```
make package
```

I was about to suggest the same thing, but since he/she already suggested that, then I simply posted the link to his/her post.

---

### Post by lovinglinux on 2010-09-08
Firefox 4.0b5 has been released yesterday!

---

### Post by Deadite81 on 2010-09-09
Hello everyone!  I have created a collection of Firefox add-ons the work correctly with Firefox 4b5 and Minefield 4b6pre on Ubuntu 10.04/10.10.  I made this because there seems to be some pretty big differences between the Windows and Linux versions of Firefox 4 (although the gap is quickly closing).  Also, I have included [FoxRunner]("https://addons.mozilla.org/en-US/firefox/addon/98430/") and [FoxTester]("https://addons.mozilla.org/en-US/firefox/addon/141505/"), which were developed by this [thread's originator]("https://addons.mozilla.org/en-US/firefox/addon/98430/developers").

These add-ons have been tested pretty thoroughly, but always remember that different combinations of add-ons can produce different effects, which I can't possibly test all by myself.  To test I use 2 profiles, a blank one (with no add-ons installed), and a duplicate of my normal profile, which has tons of junk on it.  For the most part the add-ons listed are ones I use myself, although I have tested several other popular add-ons for your convenience.

Many developers are making their add-ons compatible, but only available on their respective website, so **please be sure to read my comments!**  Also you will most certainly need the [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"), which will allow you install add-ons flagged as incompatible.

The collection is here: [https://addons.mozilla.org/en-US/firefox/collections/deadite81/add-ons-for-fx4b-on-ubuntu/](https://addons.mozilla.org/en-US/firefox/collections/deadite81/add-ons-for-fx4b-on-ubuntu/)

Sorry if this wasn't the place to put this, but it seems relevant to the thread rather than creating a whole new one :D

---

### Post by lovinglinux on 2010-09-10
> **Deadite81 said:**
> Hello everyone!  I have created a collection of Firefox add-ons the work correctly with Firefox 4b5 and Minefield 4b6pre on Ubuntu 10.05/10.10.  I made this because there seems to be some pretty big differences between the Windows and Linux versions of Firefox 4 (although the gap is quickly closing).  Also, I have included [FoxRunner]("https://addons.mozilla.org/en-US/firefox/addon/98430/") and [FoxTester]("https://addons.mozilla.org/en-US/firefox/addon/141505/"), which were developed by this [thread's originator]("https://addons.mozilla.org/en-US/firefox/addon/98430/developers").

These add-ons have been tested pretty thoroughly, but always remember that different combinations of add-ons can produce different effects, which I can possibly test all by myself.  To test I use 2 profiles, a blank one (with no add-ons installed), and a duplicate of my normal profile, which has tons of junk on it.  For the most part the add-ons listed are ones I use myself, although I have tested several other popular add-ons for your convenience.

Many developers are making their add-ons compatible, but only available on their respective website, so **please be sure to read my comments!**  Also you will most certainly need the [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"), which will all ow you install add-ons flagged as incompatible.

The collection is here: [https://addons.mozilla.org/en-US/firefox/collections/deadite81/add-ons-for-fx4b-on-ubuntu/](https://addons.mozilla.org/en-US/firefox/collections/deadite81/add-ons-for-fx4b-on-ubuntu/)

Sorry if this wasn't the place to put this, but it seems relevant to the thread rather than creating a whole new one :D

No problem. The place is totally appropriate and thanks for including FoxRunner and FoxTester.

---

### Post by ubudog on 2010-09-10
One of these days.....:)

---

### Post by fatman65535 on 2010-09-12
I have noticed some mention of having to "package" the nightlies or betas. Considering I have not bothered to "package" any of the nightly or beta builds I am using on this machine, I have to ask: *"Why?"*

This is how I keep them apart, and yet be able to use which one I want:

In /opt, there is a single directory called `firefox-4.0`; in it are two directories `beta` and `nightly`. 

In `beta are these directories: `1`, `2`, `3`, `4`, and `5`. In each of these directories is a file named `firefox-4.0b*(x)*.tar.bz2` and a directory named `firefox`.

In nightly are numerous directories, such as `2010-09-12`, `2010-09-11`, `2010-09-10`, etc. In each of these directories is a file named `firefox-4.0b*(x)*pre.en-US.linux-i686.tar.bz2` and a directory named `firefox`. 

The *(x)* represents the beta version, _pre_ refers to the nightly version. Once the `*.tar.bz2 file is downloaded, and moved to the appropriate directory; it is unpacked, and its contents go into the directory `firefox`. BTW - here is where I get the nightlies: **[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/)**.

Some quick permission changes, and the contents of the `firefox` directory are ready for use.

Each beta has its **own launcher**, and _they all use the same profile_. 

Here is the command line to launch the beta 5:

/opt/firefox-4.0/**beta**/_5_/firefox/firefox -profile /home/fatboy/data/Profiles/Bob/Firefox

and this one launched today's nightly:

/opt/firefox-4.0/**nightly**/_2010-09-12_/firefox/firefox -profile /home/fatboy/data/Profiles/Bob/Firefox

If you look carefully at the launch commands, the only differences are **bolded** and _underlined_. I am not worried about the space used for now, when you have a TB at your disposal, who cares. 

I too, noticed that `Tree Style Tabs` got broken between beta3 and beta 4. Unfortunately, that was at a time when I made the stupid mistake of updating a nightly with the latest one; **instead of doing this in the first place.**

Anyway, when it is all said and done, and the final release comes out, these nightlies and betas will get sent to the trash can.

Anyway, the icons used to represent betas and nightlies are somewhat metaphorical in context. I use a **hand grenade** (thank you [http://www.theregister.co.uk/](http://www.theregister.co.uk/) for the `gracious` use of one of your 32 pixel grenade icons). For Minefield (aka `nightliy`) I found this large picture of a round bomb with a lit fuse. I have scavenged it for the wall paper of a friend's windows^H^Hze system - picture a BSOD, with this bomb centered on top, followed with the words `NUKE ME!` laid on top of the bomb. 

He did not think it was so funny. (It is not my fault he surfs to `questionable` sites). So, for use as this icon, GIMP allowed me to scale its 576 by 520 pixel original size down to 32 by 32. It makes for a cute icon, (*ditto about the subject of the wallpaper*). Check the attachment to see what I mean.

---

### Post by lovinglinux on 2010-09-12
> **fatman65535 said:**
> I have noticed some mention of having to "package" the nightlies or betas. Considering I have not bothered to "package" any of the nightly or beta builds I am using on this machine, I have to ask: *"Why?"*

Where?

---

### Post by lovinglinux on 2010-09-14
Just received the following from Mozilla:

[LIST]
[*]Beta 6 is coming, and it will be the first beta after feature freeze. This means that no major features will be added to Firefox after this release, and all releases following it will be dedicated to fixing bugs, regressions, optimizations and cleanup. 
[*]As of Beta 5, Firefox has a new User Agent String.
[*]Firefox 4 will support the 32 and 64-bit Intel architectures on Mac, and has dropped PPC support.
[/LIST]

---

### Post by lovinglinux on 2010-09-18
Attention Firefox 4 testers!

If you install Firefox 4.0b7pre and use it with your default user profile (ppa should use a cloned one) and install new extensions or update the installed ones, they won't show up if you downgrade or switch to a previous FF version.

The thing is that FF 4.0b7pre doesn't extract the extensions xpi files anymore. It loads the extensions directly from the compressed file. When you switch back to an older FF version, which cannot read from the xpi files, these extensions won't be loaded and will not show in the addons manager.

Another thing that is about to change is the statusbar. There are some planned changes in Firefox UI that have already been discussed in several forums and blogs, that points to the removal of the statusbar, which will be replaced with a new addons bar. The address bar in FF 4.0b7pre already has the page loading status below it and the Stop/Reload buttons have been merged with the address bar. This wasn't expected during the beta phase, but it appears this change has already landed on mozilla-central, but has been backed-out due to bugs. Anyway, the next beta version will probably not include a statusbar. For those who rely on extensions that use the statusbar for launchers and user feedback (Ghostery, AdBlock Plus, NoScript and many others), be aware that your extensions might lose functionality or perhaps not even work. Many extensions will need to be adapted to work again, even if they already work with Firefox 4 Beta 6.

---

### Post by lovinglinux on 2010-09-20
A new Profile Manager is under testing. It will be a standalone application, rather than a Firefox feature and will allow to manage multiple Firefox versions and multiple profiles. This means you will be able to launch multiple Firefox versions downloaded from Mozilla using different profiles. It will also allow to create temporary profiles, which is great for testing. 

I don't know when it will be released and if the current profile manager commands will be removed from Firefox, but looks like the current profile manager will be gone.

Here is how it looks so far.

[IMG]http://tinyurl.com/2cossze[/IMG]

---

### Post by lovinglinux on 2010-09-23
Meet the addons bar:

[[IMG]http://tinyurl.com/2c9543r[/IMG]]("http://tinyurl.com/27tc6zk")

---

### Post by ubudog on 2010-09-23
Nice.

---

### Post by Frogs Hair on 2010-09-24
Do I have to disable compatibility check every time I install a new add-on ?  or every time I get an update ?  I have disabled compatibility once to get an add-on working , and if try to add others I get a message stating that the add-ons are not compatible. 4.0b7pre

---

### Post by lovinglinux on 2010-09-24
> **Frogs Hair said:**
> Do I have to disable compatibility check every time I install a new add-on ?  or every time I get an update ?  I have disabled compatibility once to get an add-on working , and if try to add others I get a message stating that the add-ons are not compatible. 4.0b7pre

Only once, if you use Addon Compatibility Reporter. If you override compatibility in **about[noparse]:[/noparse]config**, then you might need to add a new value once you switch from a beta to a pre, rc or final version, since the compatibility string includes the version. For example, these are my compatibility strings for 4.0 versions (added automatically by Addon Compatibility Reporter):

```
extensions.checkCompatibility.4.0b
extensions.checkCompatibility.4.0p
extensions.checkCompatibility.4.0pre
```

Note that they only include the first part of the version number. There is no need to add a string for 4.0b6pre and another for 4.0b7pre, but you need to add a string for 4.0b and another for 4.0pre.

Also keep in mind some extensions have a compatibility patch that needs to be downloaded. For example, when I first made my extensions compatible with FF 4 I have included the target version for 4.0b1 in the extension code. When a new beta is released, I only modify the target version in the extension code if the new version of Firefox requires additional code changes, otherwise I just change the version in the Mozilla Add-ons site. This is done so the extension doesn't need to go through the review process again, since there isn't any real code changes. When you install such extension, it might appear as incompatible after installation. If you perform the extensions update in the addons manager, the compatibility patch will be applied and the extension becomes compatible again.

---

### Post by Frogs Hair on 2010-09-24
I used about:config so I must have to add a value for each add-on. I have now installed Compatibility Reporter , which gets my Ubufox functions working.  Thanks

---

### Post by lovinglinux on 2010-09-28
[http://www.omgubuntu.co.uk/2010/09/bookmark-sync-add-on-xmarks-shutting-down-in-december/](http://www.omgubuntu.co.uk/2010/09/bookmark-sync-add-on-xmarks-shutting-down-in-december/)

I was certain that lots of users would stop using it, but I wasn't expecting a full shut down.

If you are using Firefox 4 beta, then you already have a built-in sync feature, that can sync bookmarks, passwords, tabs, settings and history. If you are using Firefox 3.5 or 3.6, then get [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/"). Time to move on and start using Mozilla's service.

If you are concerned about your privacy, delete your Xmarks account at [https://login.xmarks.com/account/delete_account](https://login.xmarks.com/account/delete_account)

---

### Post by pbenerjee on 2010-09-28
> **lovinglinux said:**
> [http://www.omgubuntu.co.uk/2010/09/bookmark-sync-add-on-xmarks-shutting-down-in-december/](http://www.omgubuntu.co.uk/2010/09/bookmark-sync-add-on-xmarks-shutting-down-in-december/)
If you are using Firefox 3.5 or 3.6, then get [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/"). Time to move on and start using Mozilla's service.


Very useful. I was wondering what to do.

---

### Post by lovinglinux on 2010-09-28
A new extension, which was released yesterday, provides the info that was displayed by the statusbar, anywhere in the addons bar or other toolbars. It's awesome!

[https://addons.mozilla.org/en-US/firefox/addon/235283/](https://addons.mozilla.org/en-US/firefox/addon/235283/)

**Note**: Doesn't work if you have Link Target Display extension enabled.

---

### Post by Frogs Hair on 2010-10-03
Hello,

I'm having a problem with AOL Radio  on FF 4 Minefield only . The music player runs fine every time on Namoroka , but when I try it on beta the page doesn't render properly. The music selection list doesn't appear.The default music selection does play but thats all .  Here are screen shots , the broken image is Minefield . Should I just chalk this one up to beta issues ?

---

### Post by lovinglinux on 2010-10-03
> **Frogs Hair said:**
> Hello,

I'm having a problem with AOL Radio  on FF 4 Minefield only . The music player runs fine every time on Namoroka , but when I try it on beta the page doesn't render properly. The music selection list doesn't appear.The default music selection does play but thats all .  Here are screen shots , the broken image is Minefield . Should I just chalk this one up to beta issues ?

Although I don't have access to AOL Radio, the list on the right appears properly. 

Looks to me is more a flash issue than a Firefox issue.

Which version of FF 4 you are using? Are you on 64bit? Which version of Flash you are using?

---

### Post by Frogs Hair on 2010-10-03
> **lovinglinux said:**
> Although I don't have access to AOL Radio, the list on the right appears properly. 

Looks to me is more a flash issue than a Firefox issue.

Which version of FF 4 you are using? Are you on 64bit? Which version of Flash you are using?

I'm using 10.1.r85 32xflash with the  wrapper this is the only site I have any problem with , Youtube at full screen and last.fm work fine.

---

### Post by lovinglinux on 2010-10-03
> **Frogs Hair said:**
> I'm using 10.1.r85 32xflash with the  wrapper this is the only site I have any problem with , Youtube at full screen and last.fm work fine.

Try with the new 64bit version of Flash.

---

### Post by Frogs Hair on 2010-10-03
If your talking about flash player square for Linux 64x I found it and I will install with Meerkat in 8 or 9  days. I can access and use the music player with Namoroka until then I'm leaving 10.04 as is until 10.10.  Thanks !

---

### Post by bailong on 2010-10-09
Anybody else having problems playing youtube videos with the new 64bit flash player? It doesn't play youtube videos at all.
I'm running 4.0b6 and Shockwave Flash 10.2 d161.

---

### Post by lovinglinux on 2010-10-09
> **bailong said:**
> Anybody else having problems playing youtube videos with the new 64bit flash player? It doesn't play youtube videos at all.
I'm running 4.0b6 and Shockwave Flash 10.2 d161.

What happens you try to access a YouTube video?

---

### Post by bailong on 2010-10-09
I just see a black square where the video should be. Works fine with FF 3.6.10.

---

### Post by bailong on 2010-10-09
Hmmm... rightclicking on the "video" and showing page source show the following:

```

<div id="watch-player" class="flash-player">

  <script>
    (function() {
      var isIE = /*@cc_on!@*/false;
      var swfHTML = (isIE) ? "<object height=\"38" + "5\" width=\"64" + "0\" classid=\"clsid:D27CDB6E-AE6D-11cf-96B8-444553540000\" id=\"movie_player\" ><param name=\"movie\" value=\"http:\/\/s.ytimg.com\/yt\/swf\/watch_as3-vfl3guoT5.swf\"><param name=\"flashvars\" value=\"rv.7.length_seconds=73&rv.6.author=MysteryGuitarMan&rv.0.length_seconds=111&rv.4.thumbnailUrl=http%3A%2F%2Fi1.ytimg.com%2Fvi%2FDewOFuiXjlU%2Fdefault.jpg&fmt_url_map=37%7Chttp%3A%2F%2Fv24.lscache5.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D37%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DC9C6699B578551CE28E2C013959C517B62ACBF9E.D43CE0F4832CC381E8A579D9AEF25CDFB66F7CE5%26id%3D25c0007222da06bc%2C22%7Chttp%3A%2F%2Fv5.lscache7.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D22%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DD7B119C9F488B7A646924512FFD9C6A6C33574B1.A4D9EFEC93A4956E87AC6E335D12D91CDDC4BE80%26id%3D25c0007222da06bc%2C35%7Chttp%3A%2F%2Fv9.lscache2.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D35%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D9D945F3CF4DEB6211891AC2F9DA74B93CFB33109.26C45DE164F1C69493D1193BA16C2FCFA14AFC90%26factor%3D1.25%26id%3D25c0007222da06bc%2C34%7Chttp%3A%2F%2Fv1.lscache4.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D34%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D178B1254DD0914806913F99385BD8C1C35CB3E89.C5F72399C15F4BA08F6B76C14AC44CA4D4608502%26factor%3D1.25%26id%3D25c0007222da06bc%2C18%7Chttp%3A%2F%2Fv7.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D18%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D09E0D32A3503796FC52FB4340395946860530575.25284E212D8554E4CFE993AC5A7E590E34118700%26factor%3D1.25%26id%3D25c0007222da06bc%2C5%7Chttp%3A%2F%2Fv3.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D5%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3DD9379ADB70BC59F20D3968AB68D8E4F6C6BA0C89.D8EC0E0A4D661C3D75ABC61C1F165F989D53EDD5%26factor%3D1.25%26id%3D25c0007222da06bc&keywords=mysteryguitarman%2Cmystery%2Cguitar%2Cman%2Cmgm%2Cjoe%2Cpenna%2Cjp&cc3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fsubtitles3_module-vflXXhUk4.swf&rv.3.rating=4.82248169404&fmt_list=37%2F1920x1080%2F9%2F0%2F115%2C22%2F1280x720%2F9%2F0%2F115%2C35%2F854x480%2F9%2F0%2F115%2C34%2F640x360%2F9%2F0%2F115%2C18%2F640x360%2F9%2F0%2F115%2C5%2F320x240%2F7%2F0%2F0&iv_storage_server=http%3A%2F%2Fwww.google.com%2Freviews%2Fy%2F&targeting_video_doc_id=&invideo=True&tk=TIRKhu1XqXrWktMF58fuvvjqZABMljNmc0OWpaEjdrMC7i7c4xUmZw%3D%3D&sffb=True&rv.5.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D2FppkdVx1H8&rv.6.length_seconds=141&timestamp=1286637656&cc_asr=1&ad_host=ca-host-pub-8914521300116825&ad_eurl=http%3A%2F%2Fwww.youtube.com%2Fvideo%2FJcAAciLaBrw&showpopout=1&mpu=True&iv_logging_level=0&endscreen_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fendscreen-vfl2yFVOn.swf&rv.0.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2FrMzr53WBDHk%2Fdefault.jpg&rv.7.author=ItalianBastards&referrer=http%3A%2F%2Fwww.youtube.com%2F&leanback_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fleanback_module-vfl_c6W8t.swf&tts_watch_url=%2Fwatch_ajax%3Faction_get_caption_track_all%26v%3DJcAAciLaBrw&rv.1.length_seconds=422&rv.3.id=y2zW6ZsDBLk&rv.2.id=MuU00Q3RhDg&rv.2.length_seconds=145&t=vjVQa1PpcFOmI5ZlGzA3TFtd_XXVpt_EesrL3AuGfrU%3D&fexp=903802%2C906402&creator=MysteryGuitarMan&allow_embed=1&fmt_stream_map=37%7Chttp%3A%2F%2Fv24.lscache5.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D37%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DC9C6699B578551CE28E2C013959C517B62ACBF9E.D43CE0F4832CC381E8A579D9AEF25CDFB66F7CE5%26id%3D25c0007222da06bc%7C%7Ctc.v24.cache5.c.youtube.com%2C22%7Chttp%3A%2F%2Fv5.lscache7.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D22%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DD7B119C9F488B7A646924512FFD9C6A6C33574B1.A4D9EFEC93A4956E87AC6E335D12D91CDDC4BE80%26id%3D25c0007222da06bc%7C%7Ctc.v5.cache7.c.youtube.com%2C35%7Chttp%3A%2F%2Fv9.lscache2.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D35%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D9D945F3CF4DEB6211891AC2F9DA74B93CFB33109.26C45DE164F1C69493D1193BA16C2FCFA14AFC90%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v9.cache2.c.youtube.com%2C34%7Chttp%3A%2F%2Fv1.lscache4.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D34%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D178B1254DD0914806913F99385BD8C1C35CB3E89.C5F72399C15F4BA08F6B76C14AC44CA4D4608502%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v1.cache4.c.youtube.com%2C18%7Chttp%3A%2F%2Fv7.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D18%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D09E0D32A3503796FC52FB4340395946860530575.25284E212D8554E4CFE993AC5A7E590E34118700%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v7.cache3.c.youtube.com%2C5%7Chttp%3A%2F%2Fv3.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D5%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3DD9379ADB70BC59F20D3968AB68D8E4F6C6BA0C89.D8EC0E0A4D661C3D75ABC61C1F165F989D53EDD5%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v3.cache3.c.youtube.com&rv.2.rating=4.87976415494&iv_enabled_features=&ad3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fad3-vfl19-Wz8.swf&rv.1.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dz2J2a3UMubM&rv.6.title=iMouth&ad_logging_flag=1&rv.1.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2Fz2J2a3UMubM%2Fdefault.jpg&ast=content&length_seconds=112&enablejsapi=1&iv_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fiv_module-vflPNQrzo.swf&rv.4.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DDewOFuiXjlU&rv.4.title=Phoenix+%28Original%29+by+TorkoalAqua&rv.5.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2F2FppkdVx1H8%2Fdefault.jpg&watermark=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Flogo-vfl_bP6ud.swf%2Chttp%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fhdlogo-vfloR6wva.swf&rv.0.title=Go+Go+Gadget&rv.3.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dy2zW6ZsDBLk&rv.7.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D1c8eoe7v7_0&rv.2.view_count=9660941&rv.4.view_count=13462&ad_channel_code_overlay=invideo_overlay_480x70_cat1%2Cafv_overlay%2Cafv_user_mysteryguitarman%2Cytps_default%2Cyt_mpvid_AASSMKx2SxFyNRmK%2Cyt_cid_521%2Cytexp_903802.906402&rv.1.view_count=1644752&dclk=True&rv.5.title=Man+In+The+Mirror&rv.1.title=Bohemian+Slide&rv.3.length_seconds=137&rv.5.author=ThatsMyTaco&rv.2.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2FMuU00Q3RhDg%2Fdefault.jpg&rv.0.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DrMzr53WBDHk&rv.0.view_count=1154743&enablecsi=1&rv.2.title=Guitar%3A+Impossible+%28stop+motion+music+short+by+MysteryGuitarMan%29&ttstrackurl=%2Fajax_timedtext%3FvideoId%3DJcAAciLaBrw%26type%3Dtrack%26lang%3Den%26name%3D&rv.3.view_count=493154&mpvid=AASSMKx2SxFyNRmK&csi_page_type=wwad&cr=US&rv.6.thumbnailUrl=http%3A%2F%2Fi1.ytimg.com%2Fvi%2FXcnPIPzOpQE%2Fdefault.jpg&host_language=en&iv3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fiv3_module-vfle9pHtr.swf&rv.7.id=1c8eoe7v7_0&rv.0.rating=4.91158804851&rv.5.id=2FppkdVx1H8&iv_load_policy=1&rv.0.id=rMzr53WBDHk&cc_font=Arial+Unicode+MS%2C+arial%2C+verdana%2C+_sans&sdetail=f%3Atopvideos%2Cp%3A%2F&rv.3.title=MGM%27s+Super+Note&sourceid=y&rv.0.author=MysteryGuitarMan&rv.3.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2Fy2zW6ZsDBLk%2Fdefault.jpg&rv.2.author=MysteryGuitarMan&rv.6.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DXcnPIPzOpQE&fmt_map=37%2F1920x1080%2F9%2F0%2F115%2C22%2F1280x720%2F9%2F0%2F115%2C35%2F854x480%2F9%2F0%2F115%2C34%2F640x360%2F9%2F0%2F115%2C18%2F640x360%2F9%2F0%2F115%2C5%2F320x240%2F7%2F0%2F0&hl=en_US&ad_flags=0&rv.5.length_seconds=143&cid=521&rv.5.view_count=11485&rv.6.id=XcnPIPzOpQE&rv.6.view_count=2364199&rv.3.author=jp&rv.4.id=DewOFuiXjlU&ttsurl=http%3A%2F%2Fvideo.google.com%2Ftimedtext%3Fsparams%3Dcaps%252Cexpire%252Cv%26expire%3D1286661600%26caps%3Dasr%26key%3Dyttt1%26signature%3DAB1631C6C3797BEAB52838DBD3DA085214620B3A.50018AC89951005FD6E5E04724D5295FF32634EC&video_id=JcAAciLaBrw&rv.4.author=TorkoalAqua&rv.7.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2F1c8eoe7v7_0%2Fdefault.jpg&ad_host_tier=22869&vq=auto&rv.7.title=Through+The+Fire+And+Flames+STOP+MOTION%21&cc_load_policy=1&rv.1.id=z2J2a3UMubM&rv.4.length_seconds=143&rv.7.view_count=138220&cafe_experiment_id=&feature=topvideos&plid=AASSMKx1IGilvcNy&afv=True&rv.5.rating=4.56666666667&ad_tag=http%3A%2F%2Fad-emea.doubleclick.net%2Fpfadx%2Fcom.ytpwatch.filmsandanimation%2Fmain_521%3Bsz%3DWIDTHxHEIGHT%3Bmpvid%3DAASSMKx2SxFyNRmK%3B%21c%3D521%3Bytexp%3D903802.906402%3Bytps%3Ddefault%3Bklg%3Den%3Bkvid%3DJcAAciLaBrw%3Bkpu%3DMysteryGuitarMan%3Bkr%3DA%3Bkt%3DK%3Bko%3Dy%3Bkpid%3D521%3Bkga%3D-1%3Bytvt%3Dw%3Bafct%3Dcontent%3Bkgg%3D-1%3Bkcr%3Dus%3Bu%3DJcAAciLaBrw%7C521%3Bafv%3D1%3Bkhd%3D1%3Bdc_dedup%3D1%3Bshortform%3D1%3B&ad_video_pub_id=ca-pub-6219811747049371&rv.1.author=MysteryGuitarMan&rv.1.rating=4.91568653658&rv.7.rating=3.27437056165&rv.2.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DMuU00Q3RhDg&ttslisturl=%2Fajax_timedtext%3FvideoId%3DJcAAciLaBrw%26type%3Dlist&cc_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fsubtitle_module-vflRC2OLC.swf&rv.6.rating=4.89243805223&sk=2ngeg6Hyj-Uz2xFla_u7QAexWOaE4hFZC&rv.4.rating=4.60736196319\"><param name=\"allowscriptaccess\" value=\"always\"><param name=\"allowfullscreen\" value=\"true\"><param name=\"bgcolor\" value=\"#000000\">\n  \n  \n  \n  <div  class=\"yt-alert yt-alert-error yt-alert-player yt-rounded\">\n      <img src=\"http:\/\/s.ytimg.com\/yt\/img\/pixel-vfl3z5WfW.gif\" class=\"icon master-sprite\" alt=\"Alert icon\">\n    \n    <div  class=\"yt-alert-content\">\n            You need Adobe Flash Player to watch this video. <br> <a href=\"http:\/\/get.adobe.com\/flashplayer\/\">Download it from Adobe.<\/a>\n    <\/div>\n    \n  <\/div>\n<\/object>" : "<embed height=\"38" + "5\" width=\"64" + "0\" type=\"application\/x-shockwave-flash\" src=\"http:\/\/s.ytimg.com\/yt\/swf\/watch_as3-vfl3guoT5.swf\" id=\"movie_player\" flashvars=\"rv.7.length_seconds=73&rv.6.author=MysteryGuitarMan&rv.0.length_seconds=111&rv.4.thumbnailUrl=http%3A%2F%2Fi1.ytimg.com%2Fvi%2FDewOFuiXjlU%2Fdefault.jpg&fmt_url_map=37%7Chttp%3A%2F%2Fv24.lscache5.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D37%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DC9C6699B578551CE28E2C013959C517B62ACBF9E.D43CE0F4832CC381E8A579D9AEF25CDFB66F7CE5%26id%3D25c0007222da06bc%2C22%7Chttp%3A%2F%2Fv5.lscache7.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D22%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DD7B119C9F488B7A646924512FFD9C6A6C33574B1.A4D9EFEC93A4956E87AC6E335D12D91CDDC4BE80%26id%3D25c0007222da06bc%2C35%7Chttp%3A%2F%2Fv9.lscache2.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D35%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D9D945F3CF4DEB6211891AC2F9DA74B93CFB33109.26C45DE164F1C69493D1193BA16C2FCFA14AFC90%26factor%3D1.25%26id%3D25c0007222da06bc%2C34%7Chttp%3A%2F%2Fv1.lscache4.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D34%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D178B1254DD0914806913F99385BD8C1C35CB3E89.C5F72399C15F4BA08F6B76C14AC44CA4D4608502%26factor%3D1.25%26id%3D25c0007222da06bc%2C18%7Chttp%3A%2F%2Fv7.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D18%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D09E0D32A3503796FC52FB4340395946860530575.25284E212D8554E4CFE993AC5A7E590E34118700%26factor%3D1.25%26id%3D25c0007222da06bc%2C5%7Chttp%3A%2F%2Fv3.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D5%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3DD9379ADB70BC59F20D3968AB68D8E4F6C6BA0C89.D8EC0E0A4D661C3D75ABC61C1F165F989D53EDD5%26factor%3D1.25%26id%3D25c0007222da06bc&keywords=mysteryguitarman%2Cmystery%2Cguitar%2Cman%2Cmgm%2Cjoe%2Cpenna%2Cjp&cc3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fsubtitles3_module-vflXXhUk4.swf&rv.3.rating=4.82248169404&fmt_list=37%2F1920x1080%2F9%2F0%2F115%2C22%2F1280x720%2F9%2F0%2F115%2C35%2F854x480%2F9%2F0%2F115%2C34%2F640x360%2F9%2F0%2F115%2C18%2F640x360%2F9%2F0%2F115%2C5%2F320x240%2F7%2F0%2F0&iv_storage_server=http%3A%2F%2Fwww.google.com%2Freviews%2Fy%2F&targeting_video_doc_id=&invideo=True&tk=TIRKhu1XqXrWktMF58fuvvjqZABMljNmc0OWpaEjdrMC7i7c4xUmZw%3D%3D&sffb=True&rv.5.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D2FppkdVx1H8&rv.6.length_seconds=141&timestamp=1286637656&cc_asr=1&ad_host=ca-host-pub-8914521300116825&ad_eurl=http%3A%2F%2Fwww.youtube.com%2Fvideo%2FJcAAciLaBrw&showpopout=1&mpu=True&iv_logging_level=0&endscreen_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fendscreen-vfl2yFVOn.swf&rv.0.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2FrMzr53WBDHk%2Fdefault.jpg&rv.7.author=ItalianBastards&referrer=http%3A%2F%2Fwww.youtube.com%2F&leanback_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fleanback_module-vfl_c6W8t.swf&tts_watch_url=%2Fwatch_ajax%3Faction_get_caption_track_all%26v%3DJcAAciLaBrw&rv.1.length_seconds=422&rv.3.id=y2zW6ZsDBLk&rv.2.id=MuU00Q3RhDg&rv.2.length_seconds=145&t=vjVQa1PpcFOmI5ZlGzA3TFtd_XXVpt_EesrL3AuGfrU%3D&fexp=903802%2C906402&creator=MysteryGuitarMan&allow_embed=1&fmt_stream_map=37%7Chttp%3A%2F%2Fv24.lscache5.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D37%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DC9C6699B578551CE28E2C013959C517B62ACBF9E.D43CE0F4832CC381E8A579D9AEF25CDFB66F7CE5%26id%3D25c0007222da06bc%7C%7Ctc.v24.cache5.c.youtube.com%2C22%7Chttp%3A%2F%2Fv5.lscache7.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D22%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DD7B119C9F488B7A646924512FFD9C6A6C33574B1.A4D9EFEC93A4956E87AC6E335D12D91CDDC4BE80%26id%3D25c0007222da06bc%7C%7Ctc.v5.cache7.c.youtube.com%2C35%7Chttp%3A%2F%2Fv9.lscache2.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D35%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D9D945F3CF4DEB6211891AC2F9DA74B93CFB33109.26C45DE164F1C69493D1193BA16C2FCFA14AFC90%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v9.cache2.c.youtube.com%2C34%7Chttp%3A%2F%2Fv1.lscache4.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D34%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D178B1254DD0914806913F99385BD8C1C35CB3E89.C5F72399C15F4BA08F6B76C14AC44CA4D4608502%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v1.cache4.c.youtube.com%2C18%7Chttp%3A%2F%2Fv7.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D18%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D09E0D32A3503796FC52FB4340395946860530575.25284E212D8554E4CFE993AC5A7E590E34118700%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v7.cache3.c.youtube.com%2C5%7Chttp%3A%2F%2Fv3.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D5%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3DD9379ADB70BC59F20D3968AB68D8E4F6C6BA0C89.D8EC0E0A4D661C3D75ABC61C1F165F989D53EDD5%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v3.cache3.c.youtube.com&rv.2.rating=4.87976415494&iv_enabled_features=&ad3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fad3-vfl19-Wz8.swf&rv.1.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dz2J2a3UMubM&rv.6.title=iMouth&ad_logging_flag=1&rv.1.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2Fz2J2a3UMubM%2Fdefault.jpg&ast=content&length_seconds=112&enablejsapi=1&iv_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fiv_module-vflPNQrzo.swf&rv.4.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DDewOFuiXjlU&rv.4.title=Phoenix+%28Original%29+by+TorkoalAqua&rv.5.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2F2FppkdVx1H8%2Fdefault.jpg&watermark=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Flogo-vfl_bP6ud.swf%2Chttp%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fhdlogo-vfloR6wva.swf&rv.0.title=Go+Go+Gadget&rv.3.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dy2zW6ZsDBLk&rv.7.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D1c8eoe7v7_0&rv.2.view_count=9660941&rv.4.view_count=13462&ad_channel_code_overlay=invideo_overlay_480x70_cat1%2Cafv_overlay%2Cafv_user_mysteryguitarman%2Cytps_default%2Cyt_mpvid_AASSMKx2SxFyNRmK%2Cyt_cid_521%2Cytexp_903802.906402&rv.1.view_count=1644752&dclk=True&rv.5.title=Man+In+The+Mirror&rv.1.title=Bohemian+Slide&rv.3.length_seconds=137&rv.5.author=ThatsMyTaco&rv.2.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2FMuU00Q3RhDg%2Fdefault.jpg&rv.0.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DrMzr53WBDHk&rv.0.view_count=1154743&enablecsi=1&rv.2.title=Guitar%3A+Impossible+%28stop+motion+music+short+by+MysteryGuitarMan%29&ttstrackurl=%2Fajax_timedtext%3FvideoId%3DJcAAciLaBrw%26type%3Dtrack%26lang%3Den%26name%3D&rv.3.view_count=493154&mpvid=AASSMKx2SxFyNRmK&csi_page_type=wwad&cr=US&rv.6.thumbnailUrl=http%3A%2F%2Fi1.ytimg.com%2Fvi%2FXcnPIPzOpQE%2Fdefault.jpg&host_language=en&iv3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fiv3_module-vfle9pHtr.swf&rv.7.id=1c8eoe7v7_0&rv.0.rating=4.91158804851&rv.5.id=2FppkdVx1H8&iv_load_policy=1&rv.0.id=rMzr53WBDHk&cc_font=Arial+Unicode+MS%2C+arial%2C+verdana%2C+_sans&sdetail=f%3Atopvideos%2Cp%3A%2F&rv.3.title=MGM%27s+Super+Note&sourceid=y&rv.0.author=MysteryGuitarMan&rv.3.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2Fy2zW6ZsDBLk%2Fdefault.jpg&rv.2.author=MysteryGuitarMan&rv.6.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DXcnPIPzOpQE&fmt_map=37%2F1920x1080%2F9%2F0%2F115%2C22%2F1280x720%2F9%2F0%2F115%2C35%2F854x480%2F9%2F0%2F115%2C34%2F640x360%2F9%2F0%2F115%2C18%2F640x360%2F9%2F0%2F115%2C5%2F320x240%2F7%2F0%2F0&hl=en_US&ad_flags=0&rv.5.length_seconds=143&cid=521&rv.5.view_count=11485&rv.6.id=XcnPIPzOpQE&rv.6.view_count=2364199&rv.3.author=jp&rv.4.id=DewOFuiXjlU&ttsurl=http%3A%2F%2Fvideo.google.com%2Ftimedtext%3Fsparams%3Dcaps%252Cexpire%252Cv%26expire%3D1286661600%26caps%3Dasr%26key%3Dyttt1%26signature%3DAB1631C6C3797BEAB52838DBD3DA085214620B3A.50018AC89951005FD6E5E04724D5295FF32634EC&video_id=JcAAciLaBrw&rv.4.author=TorkoalAqua&rv.7.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2F1c8eoe7v7_0%2Fdefault.jpg&ad_host_tier=22869&vq=auto&rv.7.title=Through+The+Fire+And+Flames+STOP+MOTION%21&cc_load_policy=1&rv.1.id=z2J2a3UMubM&rv.4.length_seconds=143&rv.7.view_count=138220&cafe_experiment_id=&feature=topvideos&plid=AASSMKx1IGilvcNy&afv=True&rv.5.rating=4.56666666667&ad_tag=http%3A%2F%2Fad-emea.doubleclick.net%2Fpfadx%2Fcom.ytpwatch.filmsandanimation%2Fmain_521%3Bsz%3DWIDTHxHEIGHT%3Bmpvid%3DAASSMKx2SxFyNRmK%3B%21c%3D521%3Bytexp%3D903802.906402%3Bytps%3Ddefault%3Bklg%3Den%3Bkvid%3DJcAAciLaBrw%3Bkpu%3DMysteryGuitarMan%3Bkr%3DA%3Bkt%3DK%3Bko%3Dy%3Bkpid%3D521%3Bkga%3D-1%3Bytvt%3Dw%3Bafct%3Dcontent%3Bkgg%3D-1%3Bkcr%3Dus%3Bu%3DJcAAciLaBrw%7C521%3Bafv%3D1%3Bkhd%3D1%3Bdc_dedup%3D1%3Bshortform%3D1%3B&ad_video_pub_id=ca-pub-6219811747049371&rv.1.author=MysteryGuitarMan&rv.1.rating=4.91568653658&rv.7.rating=3.27437056165&rv.2.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DMuU00Q3RhDg&ttslisturl=%2Fajax_timedtext%3FvideoId%3DJcAAciLaBrw%26type%3Dlist&cc_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fsubtitle_module-vflRC2OLC.swf&rv.6.rating=4.89243805223&sk=2ngeg6Hyj-Uz2xFla_u7QAexWOaE4hFZC&rv.4.rating=4.60736196319\" allowscriptaccess=\"always\" allowfullscreen=\"true\" bgcolor=\"#000000\" \/><noembed>\n  \n  \n  \n  <div  class=\"yt-alert yt-alert-error yt-alert-player yt-rounded\">\n      <img src=\"http:\/\/s.ytimg.com\/yt\/img\/pixel-vfl3z5WfW.gif\" class=\"icon master-sprite\" alt=\"Alert icon\">\n    \n    <div  class=\"yt-alert-content\">\n            You need Adobe Flash Player to watch this video. <br> <a href=\"http:\/\/get.adobe.com\/flashplayer\/\">Download it from Adobe.<\/a>\n    <\/div>\n    \n  <\/div>\n<\/noembed>";
        document.write(swfHTML);
    })();
  </script><embed type="application/x-shockwave-flash" src="http://s.ytimg.com/yt/swf/watch_as3-vfl3guoT5.swf" id="movie_player" flashvars="rv.7.length_seconds=73&amp;rv.6.author=MysteryGuitarMan&amp;rv.0.length_seconds=111&amp;rv.4.thumbnailUrl=http%3A%2F%2Fi1.ytimg.com%2Fvi%2FDewOFuiXjlU%2Fdefault.jpg&amp;fmt_url_map=37%7Chttp%3A%2F%2Fv24.lscache5.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D37%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DC9C6699B578551CE28E2C013959C517B62ACBF9E.D43CE0F4832CC381E8A579D9AEF25CDFB66F7CE5%26id%3D25c0007222da06bc%2C22%7Chttp%3A%2F%2Fv5.lscache7.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D22%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DD7B119C9F488B7A646924512FFD9C6A6C33574B1.A4D9EFEC93A4956E87AC6E335D12D91CDDC4BE80%26id%3D25c0007222da06bc%2C35%7Chttp%3A%2F%2Fv9.lscache2.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D35%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D9D945F3CF4DEB6211891AC2F9DA74B93CFB33109.26C45DE164F1C69493D1193BA16C2FCFA14AFC90%26factor%3D1.25%26id%3D25c0007222da06bc%2C34%7Chttp%3A%2F%2Fv1.lscache4.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D34%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D178B1254DD0914806913F99385BD8C1C35CB3E89.C5F72399C15F4BA08F6B76C14AC44CA4D4608502%26factor%3D1.25%26id%3D25c0007222da06bc%2C18%7Chttp%3A%2F%2Fv7.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D18%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D09E0D32A3503796FC52FB4340395946860530575.25284E212D8554E4CFE993AC5A7E590E34118700%26factor%3D1.25%26id%3D25c0007222da06bc%2C5%7Chttp%3A%2F%2Fv3.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D5%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3DD9379ADB70BC59F20D3968AB68D8E4F6C6BA0C89.D8EC0E0A4D661C3D75ABC61C1F165F989D53EDD5%26factor%3D1.25%26id%3D25c0007222da06bc&amp;keywords=mysteryguitarman%2Cmystery%2Cguitar%2Cman%2Cmgm%2Cjoe%2Cpenna%2Cjp&amp;cc3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fsubtitles3_module-vflXXhUk4.swf&amp;rv.3.rating=4.82248169404&amp;fmt_list=37%2F1920x1080%2F9%2F0%2F115%2C22%2F1280x720%2F9%2F0%2F115%2C35%2F854x480%2F9%2F0%2F115%2C34%2F640x360%2F9%2F0%2F115%2C18%2F640x360%2F9%2F0%2F115%2C5%2F320x240%2F7%2F0%2F0&amp;iv_storage_server=http%3A%2F%2Fwww.google.com%2Freviews%2Fy%2F&amp;targeting_video_doc_id=&amp;invideo=True&amp;tk=TIRKhu1XqXrWktMF58fuvvjqZABMljNmc0OWpaEjdrMC7i7c4xUmZw%3D%3D&amp;sffb=True&amp;rv.5.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D2FppkdVx1H8&amp;rv.6.length_seconds=141&amp;timestamp=1286637656&amp;cc_asr=1&amp;ad_host=ca-host-pub-8914521300116825&amp;ad_eurl=http%3A%2F%2Fwww.youtube.com%2Fvideo%2FJcAAciLaBrw&amp;showpopout=1&amp;mpu=True&amp;iv_logging_level=0&amp;endscreen_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fendscreen-vfl2yFVOn.swf&amp;rv.0.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2FrMzr53WBDHk%2Fdefault.jpg&amp;rv.7.author=ItalianBastards&amp;referrer=http%3A%2F%2Fwww.youtube.com%2F&amp;leanback_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fleanback_module-vfl_c6W8t.swf&amp;tts_watch_url=%2Fwatch_ajax%3Faction_get_caption_track_all%26v%3DJcAAciLaBrw&amp;rv.1.length_seconds=422&amp;rv.3.id=y2zW6ZsDBLk&amp;rv.2.id=MuU00Q3RhDg&amp;rv.2.length_seconds=145&amp;t=vjVQa1PpcFOmI5ZlGzA3TFtd_XXVpt_EesrL3AuGfrU%3D&amp;fexp=903802%2C906402&amp;creator=MysteryGuitarMan&amp;allow_embed=1&amp;fmt_stream_map=37%7Chttp%3A%2F%2Fv24.lscache5.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D37%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DC9C6699B578551CE28E2C013959C517B62ACBF9E.D43CE0F4832CC381E8A579D9AEF25CDFB66F7CE5%26id%3D25c0007222da06bc%7C%7Ctc.v24.cache5.c.youtube.com%2C22%7Chttp%3A%2F%2Fv5.lscache7.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Cratebypass%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26itag%3D22%26ipbits%3D0%26sver%3D3%26ratebypass%3Dyes%26expire%3D1286661600%26key%3Dyt1%26signature%3DD7B119C9F488B7A646924512FFD9C6A6C33574B1.A4D9EFEC93A4956E87AC6E335D12D91CDDC4BE80%26id%3D25c0007222da06bc%7C%7Ctc.v5.cache7.c.youtube.com%2C35%7Chttp%3A%2F%2Fv9.lscache2.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D35%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D9D945F3CF4DEB6211891AC2F9DA74B93CFB33109.26C45DE164F1C69493D1193BA16C2FCFA14AFC90%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v9.cache2.c.youtube.com%2C34%7Chttp%3A%2F%2Fv1.lscache4.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D34%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D178B1254DD0914806913F99385BD8C1C35CB3E89.C5F72399C15F4BA08F6B76C14AC44CA4D4608502%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v1.cache4.c.youtube.com%2C18%7Chttp%3A%2F%2Fv7.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D18%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3D09E0D32A3503796FC52FB4340395946860530575.25284E212D8554E4CFE993AC5A7E590E34118700%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v7.cache3.c.youtube.com%2C5%7Chttp%3A%2F%2Fv3.lscache3.c.youtube.com%2Fvideoplayback%3Fip%3D0.0.0.0%26sparams%3Did%252Cexpire%252Cip%252Cipbits%252Citag%252Calgorithm%252Cburst%252Cfactor%252Coc%253AU0dXS1ZRT19FSkNNN19OS1NH%26fexp%3D903802%252C906402%26algorithm%3Dthrottle-factor%26itag%3D5%26ipbits%3D0%26burst%3D40%26sver%3D3%26expire%3D1286661600%26key%3Dyt1%26signature%3DD9379ADB70BC59F20D3968AB68D8E4F6C6BA0C89.D8EC0E0A4D661C3D75ABC61C1F165F989D53EDD5%26factor%3D1.25%26id%3D25c0007222da06bc%7C%7Ctc.v3.cache3.c.youtube.com&amp;rv.2.rating=4.87976415494&amp;iv_enabled_features=&amp;ad3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fad3-vfl19-Wz8.swf&amp;rv.1.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dz2J2a3UMubM&amp;rv.6.title=iMouth&amp;ad_logging_flag=1&amp;rv.1.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2Fz2J2a3UMubM%2Fdefault.jpg&amp;ast=content&amp;length_seconds=112&amp;enablejsapi=1&amp;iv_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fiv_module-vflPNQrzo.swf&amp;rv.4.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DDewOFuiXjlU&amp;rv.4.title=Phoenix+%28Original%29+by+TorkoalAqua&amp;rv.5.thumbnailUrl=http%3A%2F%2Fi3.ytimg.com%2Fvi%2F2FppkdVx1H8%2Fdefault.jpg&amp;watermark=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Flogo-vfl_bP6ud.swf%2Chttp%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fhdlogo-vfloR6wva.swf&amp;rv.0.title=Go+Go+Gadget&amp;rv.3.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dy2zW6ZsDBLk&amp;rv.7.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D1c8eoe7v7_0&amp;rv.2.view_count=9660941&amp;rv.4.view_count=13462&amp;ad_channel_code_overlay=invideo_overlay_480x70_cat1%2Cafv_overlay%2Cafv_user_mysteryguitarman%2Cytps_default%2Cyt_mpvid_AASSMKx2SxFyNRmK%2Cyt_cid_521%2Cytexp_903802.906402&amp;rv.1.view_count=1644752&amp;dclk=True&amp;rv.5.title=Man+In+The+Mirror&amp;rv.1.title=Bohemian+Slide&amp;rv.3.length_seconds=137&amp;rv.5.author=ThatsMyTaco&amp;rv.2.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2FMuU00Q3RhDg%2Fdefault.jpg&amp;rv.0.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DrMzr53WBDHk&amp;rv.0.view_count=1154743&amp;enablecsi=1&amp;rv.2.title=Guitar%3A+Impossible+%28stop+motion+music+short+by+MysteryGuitarMan%29&amp;ttstrackurl=%2Fajax_timedtext%3FvideoId%3DJcAAciLaBrw%26type%3Dtrack%26lang%3Den%26name%3D&amp;rv.3.view_count=493154&amp;mpvid=AASSMKx2SxFyNRmK&amp;csi_page_type=wwad&amp;cr=US&amp;rv.6.thumbnailUrl=http%3A%2F%2Fi1.ytimg.com%2Fvi%2FXcnPIPzOpQE%2Fdefault.jpg&amp;host_language=en&amp;iv3_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fiv3_module-vfle9pHtr.swf&amp;rv.7.id=1c8eoe7v7_0&amp;rv.0.rating=4.91158804851&amp;rv.5.id=2FppkdVx1H8&amp;iv_load_policy=1&amp;rv.0.id=rMzr53WBDHk&amp;cc_font=Arial+Unicode+MS%2C+arial%2C+verdana%2C+_sans&amp;sdetail=f%3Atopvideos%2Cp%3A%2F&amp;rv.3.title=MGM%27s+Super+Note&amp;sourceid=y&amp;rv.0.author=MysteryGuitarMan&amp;rv.3.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2Fy2zW6ZsDBLk%2Fdefault.jpg&amp;rv.2.author=MysteryGuitarMan&amp;rv.6.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DXcnPIPzOpQE&amp;fmt_map=37%2F1920x1080%2F9%2F0%2F115%2C22%2F1280x720%2F9%2F0%2F115%2C35%2F854x480%2F9%2F0%2F115%2C34%2F640x360%2F9%2F0%2F115%2C18%2F640x360%2F9%2F0%2F115%2C5%2F320x240%2F7%2F0%2F0&amp;hl=en_US&amp;ad_flags=0&amp;rv.5.length_seconds=143&amp;cid=521&amp;rv.5.view_count=11485&amp;rv.6.id=XcnPIPzOpQE&amp;rv.6.view_count=2364199&amp;rv.3.author=jp&amp;rv.4.id=DewOFuiXjlU&amp;ttsurl=http%3A%2F%2Fvideo.google.com%2Ftimedtext%3Fsparams%3Dcaps%252Cexpire%252Cv%26expire%3D1286661600%26caps%3Dasr%26key%3Dyttt1%26signature%3DAB1631C6C3797BEAB52838DBD3DA085214620B3A.50018AC89951005FD6E5E04724D5295FF32634EC&amp;video_id=JcAAciLaBrw&amp;rv.4.author=TorkoalAqua&amp;rv.7.thumbnailUrl=http%3A%2F%2Fi2.ytimg.com%2Fvi%2F1c8eoe7v7_0%2Fdefault.jpg&amp;ad_host_tier=22869&amp;vq=auto&amp;rv.7.title=Through+The+Fire+And+Flames+STOP+MOTION%21&amp;cc_load_policy=1&amp;rv.1.id=z2J2a3UMubM&amp;rv.4.length_seconds=143&amp;rv.7.view_count=138220&amp;cafe_experiment_id=&amp;feature=topvideos&amp;plid=AASSMKx1IGilvcNy&amp;afv=True&amp;rv.5.rating=4.56666666667&amp;ad_tag=http%3A%2F%2Fad-emea.doubleclick.net%2Fpfadx%2Fcom.ytpwatch.filmsandanimation%2Fmain_521%3Bsz%3DWIDTHxHEIGHT%3Bmpvid%3DAASSMKx2SxFyNRmK%3B%21c%3D521%3Bytexp%3D903802.906402%3Bytps%3Ddefault%3Bklg%3Den%3Bkvid%3DJcAAciLaBrw%3Bkpu%3DMysteryGuitarMan%3Bkr%3DA%3Bkt%3DK%3Bko%3Dy%3Bkpid%3D521%3Bkga%3D-1%3Bytvt%3Dw%3Bafct%3Dcontent%3Bkgg%3D-1%3Bkcr%3Dus%3Bu%3DJcAAciLaBrw%7C521%3Bafv%3D1%3Bkhd%3D1%3Bdc_dedup%3D1%3Bshortform%3D1%3B&amp;ad_video_pub_id=ca-pub-6219811747049371&amp;rv.1.author=MysteryGuitarMan&amp;rv.1.rating=4.91568653658&amp;rv.7.rating=3.27437056165&amp;rv.2.url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DMuU00Q3RhDg&amp;ttslisturl=%2Fajax_timedtext%3FvideoId%3DJcAAciLaBrw%26type%3Dlist&amp;cc_module=http%3A%2F%2Fs.ytimg.com%2Fyt%2Fswf%2Fsubtitle_module-vflRC2OLC.swf&amp;rv.6.rating=4.89243805223&amp;sk=2ngeg6Hyj-Uz2xFla_u7QAexWOaE4hFZC&amp;rv.4.rating=4.60736196319" allowscriptaccess="always" allowfullscreen="true" bgcolor="#000000" height="385" width="640"><noembed>
  
  
  &lt;div  class="yt-alert yt-alert-error yt-alert-player yt-rounded"&gt;
      &lt;img src="http://s.ytimg.com/yt/img/pixel-vfl3z5WfW.gif" class="icon master-sprite" alt="Alert icon"&gt;
    
    &lt;div  class="yt-alert-content"&gt;
            You need Adobe Flash Player to watch this video. &lt;br&gt; &lt;a href="http://get.adobe.com/flashplayer/"&gt;Download it from Adobe.&lt;/a&gt;
    &lt;/div&gt;
    
  &lt;/div&gt;
</noembed>

      </div>
```Looks like youtube doesn't recognize the flash plugin.

---

### Post by lovinglinux on 2010-10-09
> **bailong said:**
> I just see a black square where the video should be. Works fine with FF 3.6.10.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by bailong on 2010-10-09
Thanks for your help already, here are the required info:

Flash path and version:

[FONT=Courier New]File:  /usr/lib/mozilla/plugins/libflashplayer.so
Version: Shockwave Flash 10.2 d161

application/x-shockwave-flash Shockwave Flash swf [/FONT] [FONT=Courier New]
  application/futuresplash FutureSplash Player spl[/FONT]

Firefox Version is

[FONT=Courier New]Mozilla/5.0 (X11; Linux i686 on x86_64; rv:2.0b6) Gecko/20100101 Firefox/4.0b6[/FONT]

firefox-report.txt is attached.

---

### Post by oldos2er on 2010-10-09
> **bailong said:**
> Anybody else having problems playing youtube videos with the new 64bit flash player? 

It's been working great for me. How did you install it?

---

### Post by bailong on 2010-10-09
> **oldos2er said:**
> It's been working great for me. How did you install it?

I was using flash aid in FF 3.6.10, in the FF 4.0b6 startscript I pointed 

[FONT=Courier New]moz_libdir[/FONT]

to

[FONT=Courier New]/usr/lib/firefox-3.6.10[/FONT]

---

### Post by lovinglinux on 2010-10-09
Disable sevenmachines flash ppa, then do this:

```
sudo apt-get purge flashplugin64-installer
```

The run FLASH-AID again and choose the 64bit version.

---

### Post by bailong on 2010-10-09
There we go:

[FONT=Courier New]LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]

[FONT=Verdana]EDIT: posted at the samne time as you did lovinglinux[/FONT]
[/FONT]

---

### Post by lovinglinux on 2010-10-09
Disable sevenmachines flash ppa, then do this:

```
sudo apt-get purge flashplugin64-installer
```

The run FLASH-AID again and choose the 64bit version.

Also make sure you are running version 1.0.14 of FLASH-AID, because versions 1.0.13 and older no longer work with the 64bit plugin.

---

### Post by bailong on 2010-10-09
Meh:
[FONT=Courier New]
bailong@apollo:~/Downloads$ file firefox-4.0b6/firefox-bin 
firefox-4.0b6/firefox-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped[/FONT]

Sorry :(

---

### Post by bailong on 2010-10-09
Am I missing something? Just downloaded FF 4.0b6 for Linux i686 from mozilla.org but still getting:

[FONT=Courier New]bailong@apollo:~/Downloads$ file firefox/firefox-bin 
firefox/firefox-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped[/FONT]

---

### Post by lovinglinux on 2010-10-09
> **bailong said:**
> Meh:
[FONT=Courier New]
bailong@apollo:~/Downloads$ file firefox-4.0b6/firefox-bin 
firefox-4.0b6/firefox-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped[/FONT]

Sorry :(

Yeah, I was about to post that too.

```
Mozilla/5.0 (X11; Linux **i686** on x86_64; rv:2.0b6) Gecko/20100101 Firefox/4.0b6
```

Nevertheless, I would recommend doing the steps from my previous post, because you are using the plugin from sevenmachines and not from FLASH-AID.

---

### Post by lovinglinux on 2010-10-09
> **bailong said:**
> Am I missing something? Just downloaded FF 4.0b6 for Linux i686 from mozilla.org but still getting:

[FONT=Courier New]bailong@apollo:~/Downloads$ file firefox/firefox-bin 
firefox/firefox-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped[/FONT]

The 32bit Firefox won't recognize the plugin. You need to install the 64bit version of Firefox 4.

---

### Post by bailong on 2010-10-09
This is embarrassing, not my day I guess. i686 != x86_64. Thanks for your help, installed 64bit FF and everything works great.

---

### Post by lovinglinux on 2010-10-09
> **bailong said:**
> This is embarrassing, not my day I guess. i686 != x86_64. Thanks for your help, installed 64bit FF and everything works great.

No problem. When I first read your report I suspected you could be using a 32bit version, but I read **x86_64** in the user agent string and moved on, without realizing there was an i686 before it. So it is my fault too :)

---

### Post by lovinglinux on 2010-10-20
[Firefox 4 extensions to make it behave like Firefox 3.6]("http://ubuntuforums.org/showthread.php?t=1601868")

---

### Post by QwUo173Hy on 2010-10-28
How do I enable accelerated graphics, and test that they're working?

---

### Post by lovinglinux on 2010-10-28
> **jarlath said:**
> How do I enable accelerated graphics, and test that they're working?

I'm afraid you need to compile it. 

[http://blog.mozilla.com/joe/2010/09/15/so-you-want-to-help-us-with-hardware-acceleration/](http://blog.mozilla.com/joe/2010/09/15/so-you-want-to-help-us-with-hardware-acceleration/)

Test:

[http://demos.hacks.mozilla.org/openweb/HWACCEL/](http://demos.hacks.mozilla.org/openweb/HWACCEL/)

I get 5 FPS in a vanilla Firefox 4.0b8pre, 13 FPS in Opera 11.0 alpha build 1029 and 13 FPS in Chrome 8.0.552.18 dev.

---

### Post by QwUo173Hy on 2010-10-29
> **lovinglinux said:**
> I'm afraid you need to compile it. 

[http://blog.mozilla.com/joe/2010/09/15/so-you-want-to-help-us-with-hardware-acceleration/](http://blog.mozilla.com/joe/2010/09/15/so-you-want-to-help-us-with-hardware-acceleration/)

Test:

[http://demos.hacks.mozilla.org/openweb/HWACCEL/](http://demos.hacks.mozilla.org/openweb/HWACCEL/)

I get 5 FPS in a vanilla Firefox 4.0b8pre, 13 FPS in Opera 11.0 alpha build 1029 and 13 FPS in Chrome 8.0.552.18 dev.
Ouch! Thanks, I might give it a try in the future :)

---

### Post by lovinglinux on 2010-11-10
> **jarlath said:**
> How do I enable accelerated graphics, and test that they're working?

The latest nightly build comes with an option to enable hardware acceleration in the advanced preferences.

---

### Post by QwUo173Hy on 2010-11-10
> **lovinglinux said:**
> The latest nightly build comes with an option to enable hardware acceleration in the advanced preferences.

That's great lovinglinux, thanks for that. It's good to hear it's making it's way in. I thought it might remain something that had to be hacked for linux users.

---

### Post by lovinglinux on 2010-11-10
> **jarlath said:**
> That's great lovinglinux, thanks for that. It's good to hear it's making it's way in. I thought it might remain something that had to be hacked for linux users.

I guess so, because I just received the news about Beta 7 release and it only talks about Win and Mac in regard to HA.

[http://blog.mozilla.com/blog/2010/11/10/fasten-your-seatbelts-latest-firefox-4-beta-boosts-speed-in-the-browser/](http://blog.mozilla.com/blog/2010/11/10/fasten-your-seatbelts-latest-firefox-4-beta-boosts-speed-in-the-browser/)

I'm not sure it even works with my card, but with Opera I get 13 FPS and Firefox 8 FPS. Both ridiculously slow anyway.

---

### Post by emarkay on 2010-12-10
Just checking in here.
I have current nightly working fine: 
Mozilla/5.0 (X11; Linux i686; rv:2.0b8pre) Gecko/20101210 Firefox/4.0b8pre

Only a few Add-ons not working, nothing critical (important ones work fine, NoScript, BetterPrivacy, Flashblock...)

Don't see much of any difference in use ( stability, speed, display, etc.) compared to 3.6x, aside from a few "different ways to do things" , but looks like this'll be a transparent upgrade for me when it's official.

Thanks!

---

### Post by SilverWave on 2010-12-11
[reposted to correct group] [here]("http://ubuntuforums.org/showthread.php?p=10229093#post10229093")

---

### Post by SilverWave on 2010-12-11
[reposted to correct group] [here]("http://ubuntuforums.org/showthread.php?p=10229093#post10229093")

---

### Post by libssd on 2010-12-12
Would I be correct to assume that the Silverwave PPA is no longer available for Firefox test releases? If I add this repository: ppa:silverwave/one-daily-a-month-1

apt-get update returns an error message about the repository not being available. [as of ~1900 EST, December 12]

**UPDATE**: Seems OK now [1950 EST]

I'm trying to figure out how to get automatic updates to FF 4.0 without also updating FF 3.6 to Namaroka, as happens if the ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu repository is active. This is a minor annoyance, and I can undo the Namaroka upgrade, but I would prefer to have only one testing version of FF installed at a time.

---

### Post by lovinglinux on 2010-12-13
> **libssd said:**
> I'm trying to figure out how to get automatic updates to FF 4.0 without also updating FF 3.6 to Namaroka, as happens if the ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu repository is active. This is a minor annoyance, and I can undo the Namaroka upgrade, but I would prefer to have only one testing version of FF installed at a time.

Disable the ubuntu-mozilla-daily, reinstall Firefox and then use SilverWave ppa to get Firefox 4.

---

### Post by libssd on 2010-12-13
Thanks for the confirmation. Unfortunately, when I try that approach, I get an unmet dependencies error.

---

### Post by lovinglinux on 2010-12-13
> **libssd said:**
> Thanks for the confirmation. Unfortunately, when I try that approach, I get an unmet dependencies error.

When, while trying to install Firefox 4 or when reinstalling Firefox 3.6?

---

### Post by libssd on 2010-12-13
> **lovinglinux said:**
> When, while trying to install Firefox 4 or when reinstalling Firefox 3.6?
1. De-activate [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) (Synaptic)
2. Activate [http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu](http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu) (Synaptic)
3. Uninstall firefox-4.0(Synaptic)
4. sudo apt-get update (terminal)
5. sudo apt-get install firefox-4.0 (terminal or synaptic, dependency errors)

---

### Post by lovinglinux on 2010-12-13
> **libssd said:**
> 1. De-activate [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) (Synaptic)
2. Activate [http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu](http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu) (Synaptic)
3. Uninstall firefox-4.0(Synaptic)
4. sudo apt-get update (terminal)
5. sudo apt-get install firefox-4.0 (terminal or synaptic, dependency errors)

You should report this to SilverWave.

[http://ubuntuforums.org/showthread.php?t=1352580](http://ubuntuforums.org/showthread.php?t=1352580)

---

### Post by BigCityCat on 2011-01-08
Okay firefox 4 is shaping up now. The only thing I hate is the ugly *** bookmarks icon. I just went with text only. I hope they change the default icon.

---

### Post by areteichi on 2011-01-16
OK, since most of the add-ons I use now have the Firefox 4 support, I decided to start using Firefox 4 as the default browser from today.

But as I started using it, I noticed something funny with the setting. When I go into > about: config
I no longer see these settings as I used to with Firefox 3.6> browser.history_expire_days 2
browser.history_expire_days_min 2
browser.history_expire_sites 10000
What I want to basically do is to set Firefox so that it will delete the browsing history that is older than 2 days. Is this no longer possible with Firefox 4? Why would they take this feature away...?

I'm using Firefox 4b10pre from Mozilla Daily PPA on Maverick.

---

### Post by areteichi on 2011-01-16
Oh, and another problem I forgot to mention is the YouTube preview feature in Gmail. It seems like the YouTube preview doesn't work properly under Firefox 4. A small picture from the video just pops up in a new tab/window and I can't play the video from Gmail. Embedded videos basically becomes a new tab and I need to play it from there. It's very strange...

---

### Post by lovinglinux on 2011-01-16
> **areteichi said:**
> OK, since most of the add-ons I use now have the Firefox 4 support, I decided to start using Firefox 4 as the default browser from today.

But as I started using it, I noticed something funny with the setting. When I go into 
I no longer see these settings as I used to with Firefox 3.6
What I want to basically do is to set Firefox so that it will delete the browsing history that is older than 2 days. Is this no longer possible with Firefox 4? Why would they take this feature away...?

I'm using Firefox 4b10pre from Mozilla Daily PPA on Maverick.

Indeed it seems those options have been removed. you need to clear your history manually.

> **areteichi said:**
> Oh, and another problem I forgot to mention is the YouTube preview feature in Gmail. It seems like the YouTube preview doesn't work properly under Firefox 4. A small picture from the video just pops up in a new tab/window and I can't play the video from Gmail. Embedded videos basically becomes a new tab and I need to play it from there. It's very strange...

Check if you are allowing third-party cookies.

---

### Post by areteichi on 2011-01-17
> **lovinglinux said:**
> Check if you are allowing third-party cookies.

Thanks! I was allowing the third-party cookies but I found out that this was caused by NoScript. The problem seems to have solved when I turned off the ABE (application boundary enforcer) option in NoScript. What I'm finding strange is I had this option enabled in Firefox 3.6 and I didn't experience this. It seems to be working anyway.

Regarding the browser history, do you know what these values do?
> browser.history.maxStateObjectSize  655360
places.history.expiration.transient_current_max_pages  63018
Even if we can no longer configure Firefox to delete the browsing history by the number of days, I'm wondering either of these values sets the upper limit as to how many objects it will store.

---

### Post by lovinglinux on 2011-01-17
> **areteichi said:**
> Regarding the browser history, do you know what these values do?

Try [http://kb.mozillazine.org](http://kb.mozillazine.org)

---

### Post by areteichi on 2011-01-17
Mozilla apparently decided to change the way Firefox handles the browsing history. I guess Firefox now automatically determines how much history will be stored depending on your browsing habits or something.

[http://blog.bonardo.net/2010/01/20/places-got-async-expiration](http://blog.bonardo.net/2010/01/20/places-got-async-expiration)
[https://wiki.mozilla.org/Firefox/Projects/Places_async_expiration](https://wiki.mozilla.org/Firefox/Projects/Places_async_expiration)

I don't have any problems with this new algorithm, but I still don't see why they needed to take away the old feature? I don't need more than two days of history... (and I'm quite positive Firefox won't delete it within a few days) I guess there's more manual labor for me to do...

EDIT:
I'm going to take a bit of risk and try the possible workaround I found from the following thread:
[http://forums.mozillazine.org/viewtopic.php?f=23&t=2057651](http://forums.mozillazine.org/viewtopic.php?f=23&t=2057651)

Basically I'm going to create the following value (as integer)
> places.history.expiration.max_pages
and set it to 200. I will test and see if this will do the job.

---

### Post by libssd on 2011-01-17
I think this will do what you want:

```
browser.history_expire_days.mirror   user set   integer   180
```
Default value is 180; try changing it to 5 and see what happens.

---

### Post by lovinglinux on 2011-01-17
> **areteichi said:**
> I don't have any problems with this new algorithm, but I still don't see why they needed to take away the old feature? I don't need more than two days of history... (and I'm quite positive Firefox won't delete it within a few days) I guess there's more manual labor for me to do...

I guess because of the sync feature. They are trying to reduce user interaction in some areas and the sync was the first one to use that approach.

---

### Post by areteichi on 2011-01-17
> **libssd said:**
> I think this will do what you want:

```
browser.history_expire_days.mirror   user set   integer   180
```
Default value is 180; try changing it to 5 and see what happens.

Thank you for your suggestion. Indeed that is how I was configuring the browsing history in Firefox 3.6, but unfortunately that value is no longer available in Firefox 4. The closest setting I am able to configure is the value I mentioned above, so I guess I will adjust that to suit my needs and see if it will do the job.

---

### Post by areteichi on 2011-01-22
Just to update on my previous posts:

> places.history.expiration.max_pages
This setting does seem to do the trick. As far as I can tell, this limits the amount of browsing history Firefox will store by the number of entries (as oppose to the elapsed time). After spending the past few days experimenting with it, I now have the value set to _2000_ which seems to limit the browsing history only to a few days :p (This is obviously based on my own browsing frequency.)

However, I've actually been experiencing another minor issue. I don't know if anyone else has come across this, but the Firefox UI seems to glitch occasionally for no particular reason. Some of the icons on the toolbars and the texts on the displayed website suddenly disappear or get distorted. (They become visible when I hover my mouse over, but soon become invisible again.) Although things usually revert to normal after I relaunch Firefox, I also realized that there are cases where some characters remain distorted even after I close Firefox that the distorted characters affect the GNOME environment as a whole. (Hence, I've seen GNOME menu with these distorted characters.)

Since I also saw glitches outside of Firefox, I thought it could be the hardware acceleration that is causing this. So I disabled it in the preferences, but this issue still persists. (It just happened as I was typing this sentence...) Very strange indeed. :icon_frown:

Does anyone have a clue? :-k

---

### Post by Deadite81 on 2011-01-23
This "distortion" also happens to me, especially in text boxes and in the add-on manager.  I haven't noticed it outside of Firefox, but sometimes restarting doesn't fix it and I have to log out and in.

Also, sometimes the add-on manager simply won't work at all and freezes Firefox completely.  If I use Bleachbit to "vacuum" the databases then everything works again for a while.  I'm using an Nvidia 6200 with the latest proprietary driver and Compiz.

---

### Post by areteichi on 2011-01-23
I'm using Ubuntu 10.10 with Intel 950 GMA Grahics Chip (945GM Chipset) and Compiz enabled. Could Compiz have something to do with this?

Yeah I also use BleachBit occasionally to clean up the sqlite databases, but I still experience this issue in spite of that. It's quite unlikely that this will get fixed prior to the final release isn't it? There just aren't enough FF4 users at the moment to get clear about the cause of this problem.

---

### Post by Deadite81 on 2011-01-23
Hard to say.  I'm using an Intel chip as well.  With the Nvidia driver installed I have to use Compiz.  When I use Metacity I eventually get lots of graphical glitches and have to restart. On the other hand, when I use Compiz I eventually have to log out and in because window contents take forever to load.  It's not the same rendering issue as with Firefox, but Nvidia just seems to be problematic in general for me.

I get no errors of importance in the FF Error Console, but when the Add-on Manager is about to crap out I get a zillion GTK+ errors.  Bleachbit fixes it, but it doesn't fix the graphical glitches.  I assume it has to do with Compiz rather than FF, but really have no idea... Maybe it will be fixed, maybe not.  I've searched and search for info, but have found nothing about either issue.  If you learn anything please let me know!

---

### Post by areteichi on 2011-01-24
Here is a screenshot:

[[IMG]http://tetsudo.files.wordpress.com/2011/01/screenshot.png?w=300&h=187[/IMG]]("http://tetsudo.files.wordpress.com/2011/01/screenshot.png")

As you can see, the letter "B" is garbled and the "A" is missing from "Art". This never used to happen before I switched to FF4. Since this isn't the only symptom to this problem, I will try to post more screenshots when I come across other ones.

---

### Post by Deadite81 on 2011-01-24
This is not the same problem I have.  I see that the b's are all shaped like the same symbol, and you say it happens outside of FF.  I am willing to bet it's some sort of locale issue or font problem.  Have you tried changing fonts?  Do you switch dialects?

---

### Post by areteichi on 2011-01-24
> **Deadite81 said:**
> This is not the same problem I have.  I see that the b's are all shaped like the same symbol, and you say it happens outside of FF.  I am willing to bet it's some sort of locale issue or font problem.  Have you tried changing fonts?  Do you switch dialects?

Thanks for your prompt reply :p

Although I'm not completely sure what sort of issues you're having, I still think mine is related more to the graphics than to the character-encodings, locales, or fonts. I see texts disappearing and menus turning black, which to me seem unrelated to the font/language configuration issue.

In any case, the default language is set to English, and I have installed Japanese in addition. I do customize ~/.font.conf in order to enable the font rendering and anti-aliasing for the Japanese fonts. But I've been using this custom configuration for the past 3-4 Ubuntu releases and I have never encountered this issue before.

Plus, I seem to encounter this problem only when I'm running FF4. Although the glitch can affect the desktop environment as well, that's only after the glitch occurs in FF4. In other words, FF4 seems to be affecting the desktop environment and not vice versa.

By the way, I just turned off Compiz but I'm still seeing the same symptoms. :-?

---

### Post by areteichi on 2011-01-24
I figured out a way to replicate the problem (at least one of its effects). When I have FF4 minimized and try to maximize it, I get the tearing on the screen.

Actually, since Wordpress is entirely based on Javascript (I think...), I don't even see anything when I try to maximize the screen. The parts that have appeared on the screenshots are due to hovering my mouse over those parts of the screen.

[[IMG]http://tetsudo.files.wordpress.com/2011/01/screenshot1.png?w=300&h=187]("http://tetsudo.files.wordpress.com/2011/01/screenshot1.png")[/IMG]

[[IMG]http://tetsudo.files.wordpress.com/2011/01/screenshot-1.png?w=300&h=187[/IMG]]("http://tetsudo.files.wordpress.com/2011/01/screenshot-1.png")

[[IMG]http://tetsudo.files.wordpress.com/2011/01/screenshot-2.png?w=300&h=187[/IMG]]("http://tetsudo.files.wordpress.com/2011/01/screenshot-2.png")

[[IMG]http://tetsudo.files.wordpress.com/2011/01/screenshot-4.png?w=300&h=187[/IMG]]("http://tetsudo.files.wordpress.com/2011/01/screenshot-4.png")

I'm suspecting my problem is related to the way FF4 handles Javascript...?

---

### Post by Deadite81 on 2011-01-24
Wow.  Your problem is similar to mine, only waaaaaaaaay more amplified!  Based on your previous posts I was testing stuff to see if I could recreate your problem, but I now see that I was going in the complete wrong direction.

A couple questions:

Are you using Firefox 4 from the Mozilla Daily PPA or are you using it independently of your package manager?  I prefer to use it independently, that is, directly downloading it and running it from my home folder.  This way I get incremental updates.  I was just checking out the MD PPA on Launchpad and they've had some build errors, so that could be an issue.

Which Java plugin are you using?  OpenJDK or Sun/Oracle?  I see you are using the Zotero addon, and it's my understanding that Zotero has problems with OpenJDK.  I have also experienced many other OpenJDK problems in the past.

Do you have the profile manager installed?  If so, have you tried to recreate your problem using a black profile?  (I recommend trying that!)

---

### Post by areteichi on 2011-01-24
> **Deadite81 said:**
> Wow.  Your problem is similar to mine, only waaaaaaaaay more amplified!  Based on your previous posts I was testing stuff to see if I could recreate your problem, but I now see that I was going in the complete wrong direction.

A couple questions:

Are you using Firefox 4 from the Mozilla Daily PPA or are you using it independently of your package manager?  I prefer to use it independently, that is, directly downloading it and running it from my home folder.  This way I get incremental updates.  I was just checking out the MD PPA on Launchpad and they've had some build errors, so that could be an issue.

Which Java plugin are you using?  OpenJDK or Sun/Oracle?  I see you are using the Zotero addon, and it's my understanding that Zotero has problems with OpenJDK.  I have also experienced many other OpenJDK problems in the past.

Do you have the profile manager installed?  If so, have you tried to recreate your problem using a black profile?  (I recommend trying that!)

Just to let you know, these screenshots illustrate the problem in their worst possible case. For most of the websites I visit, FF4 works quite well and is much more responsive than 3.6. It was just that I discovered that Wordpress shows the problem at its worst and is also replicable, I thought I would post the screenshots to illustrate what sort of problems I'm having.

I am actually using PPA, as I think there is more integration with the DE (I suppose with the firefox-4.0-gnome-support package). As you pointed out, I haven't been receiving updates from the Mozilla PPA due to build failures, but I certainly don't have a broken version installed. (I think Launchpad automatically ignores failed builds.)

I use Sun Java precisely for Zotero reasons. I have both installed but I'm guessing Sun Java is being used? I have no problems with Zotero, though the database was getting a little buggy so I rebuilt it a couple days a go using sqlite dump & vacuum.

Lastly, yes I did try my PPA FF4 with add-ons disabled and also with a fresh profile, and the same issue arises with both. But I don't have this problem with FF3.6 nor Chromium. So it's not the problem with Flash nor Ubuntu, and I'm quite positive that it is FF4 that is the cause of all this.

Hopefully someone has already filed a bug related to this and is being worked on. (I looked for such a bug but couldn't find it - but that may just be cause I don't quite know how to phrase the problem when searching for it)

---

### Post by areteichi on 2011-01-25
> **Deadite81 said:**
> Are you using Firefox 4 from the Mozilla Daily PPA or are you using it independently of your package manager?  I prefer to use it independently, that is, directly downloading it and running it from my home folder.  This way I get incremental updates.  I was just checking out the MD PPA on Launchpad and they've had some build errors, so that could be an issue.

You're absolutely right! I gave the independent version (Mozilla's tar.gz version) a try and it didn't have this problem!! Again, I don't think I will use this Mozilla version since it is does not integrate with the rest of the system, but it is certainly great to know that this might just be a temporary issue with the PPA build.

PPA builds have been failing for the past 4 days so I really hope they can give me an update soon (and solve this damn issue!)

Also, Beta 10 just came out: [http://www.mozilla.com/en-US/firefox/4.0b10/releasenotes/](http://www.mozilla.com/en-US/firefox/4.0b10/releasenotes/)

---

### Post by Deadite81 on 2011-01-25
Good I'm glad you got it working, as I was otherwise stumped.  And Bugzilla isn't the easiest thing to navigate for a mere mortal.  Yes, it's true that Launchpad ignores failed builds, but so many failed that I felt it could be indicative of other problems, especially since other related packages *didn't *fail.

Consequently, I haven't had any more problems on my side, so it looks like they're working out the kinks!

---

### Post by areteichi on 2011-01-26
Glad to hear you got your problem solved! :razz:

Since today's PPA build failed again, I just pulled the Firefox 4 packages from Natty (not recommended!!! - but I still do that sometimes :-\") and the problems are gone! It's fully integrated into my system now too! (completely replaced FF3.6) Although it's still Beta 9, it's working very well. I'm much more satisfied now.

---

### Post by Frogs Hair on 2011-03-06
I switched back to Minefield because the release candidate is out and I have a question . Where is the location to check to see what plug-ins are activated . I know where installed plug-ins are listed what am looking for is the active plug-ins list as is in Firefox 3.6.XX  .

---

### Post by libssd on 2011-03-07
So, what happens when FF 4.0 production is released? Does it automatically replace 3.6? Or, do I remove 3.6, then install 4.0 from a repository? 

For me, this is somewhat of an academic question, as Chrome has become my default browser, in large part because I'm participating in the Chrome OS pilot program. But it's always good to have an alternative.

---

### Post by Frogs Hair on 2011-03-07
> **libssd said:**
> So, what happens when FF 4.0 production is released? Does it automatically replace 3.6? Or, do I remove 3.6, then install 4.0 from a repository? 

For me, this is somewhat of an academic question, as Chrome has become my default browser, in large part because I'm participating in the Chrome OS pilot program. But it's always good to have an alternative.

If 4.0 is released released before Ubuntu 11.04 it should be included . I don't know if Ubuntu operating systems that include 3.6.XX will have an upgrade option via the update manager . I have been using the Mozilla daily  PPA  so I have had development releases for the past year.

---

### Post by lovinglinux on 2011-03-08
> **Frogs Hair said:**
> I switched back to Minefield because the release candidate is out and I have a question . Where is the location to check to see what plug-ins are activated . I know where installed plug-ins are listed what am looking for is the active plug-ins list as is in Firefox 3.6.XX  .

Tools > Add-ons

---

### Post by Frogs Hair on 2011-03-08
> **lovinglinux said:**
> Tools > Add-ons

That gives me a list of installed and enabled plug-ins as I wrote , It does not show what plug-ins are currently active.

---

### Post by lovinglinux on 2011-03-09
> **Frogs Hair said:**
> That gives me a list of installed and enabled plug-ins as I wrote , It does not show what plug-ins are currently active.

Oh, I see. Sorry.

Visit [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

or

[http://www.mozilla.com/en-US/plugincheck/](http://www.mozilla.com/en-US/plugincheck/)

You can determine which one is active by the version displayed on those pages. However, if you have multiple instances of the same version, then I don't know how to determine the one is active. Keep in mind that the plugin saved under ~/.mozilla/plugins will have precedence over the one installed in the system folder.

BTW, in you question you say you wanted to see the list of activated plugins like in Firefox 3.6, but there is no difference between Firefox 4 and 3.6 for that matter. If you are referring to **about[noparse]:[/noparse]plugins**, it only shows the information displayed on Tools > Add-ons in more detail.

---

### Post by Frogs Hair on 2011-03-09
> **lovinglinux said:**
> Oh, I see. Sorry.

Visit [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

or

[http://www.mozilla.com/en-US/plugincheck/](http://www.mozilla.com/en-US/plugincheck/)

You can determine which one is active by the version displayed on those pages. However, if you have multiple instances of the same version, then I don't know how to determine the one is active. Keep in mind that the plugin saved under ~/.mozilla/plugins will have precedence over the one installed in the system folder.

BTW, in you question you say you wanted to see the list of activated plugins like in Firefox 3.6, but there is no difference between Firefox 4 and 3.6 for that matter. If you are referring to **about[noparse]:[/noparse]plugins**, it only shows the information displayed on Tools > Add-ons in more detail.

I will install Namoroka and show you what I mean. There is a plug-in indicator  that shows on the status bar in FF 3.6 XX . When the plug-in icon is selected it displays a list of all plug-ins and active plug-ins , so if totem or flash is in use they show on the active list. I can't locate this in Minefield , even with the add-on bar enabled.

---

### Post by Frogs Hair on 2011-03-09
This is what I was writing about . It does not appear on Minefield.

---

### Post by lovinglinux on 2011-03-10
> **Frogs Hair said:**
> This is what I was writing about . It does not appear on Minefield.

Oh I see, that little icon that pops up in the statusbar when you are viewing a flash video. I have been using Firefox 4 for so long that I totally forgot about it.

I guess it has been removed, since there is no more statusbar, but I don't know if it can be accessed elsewhere.

---

### Post by lovinglinux on 2011-03-10
Firefox 4 Release Candidate is out.

[http://www.mozilla.com/en-US/firefox/RC/](http://www.mozilla.com/en-US/firefox/RC/)

---

### Post by Frogs Hair on 2011-03-10
> **lovinglinux said:**
> Oh I see, that little icon that pops up in the statusbar when you are viewing a flash video. I have been using Firefox 4 for so long that I totally forgot about it.

I guess it has been removed, since there is no more statusbar, but I don't know if it can be accessed elsewhere.

I was playing with Moonlight again and I was trying to see if it was active and I found a test site and it worked .

I am unable to use a site that requires it , so I disabled adblock and no script and it still doesn't work . Moonlight failed on the same site the last time I tried it so it it has been removed .

---

