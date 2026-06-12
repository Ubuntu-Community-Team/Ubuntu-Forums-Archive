---
title: "A bit of help - non-free, codecs, restricted &amp; Adobe"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by virtualu2 on 2009-09-28
Hi,
I am new to Koala and somewhat new to Ubuntu, but OK with Linux and quite technical.

I am trying to find out the best method to install the codecs, restricted extras, Sun Java plugin, Mplayer for Mozilla, Adobe Flash, Adobe Air, and TweetDeck on Ubuntu 32bit Koala.

I know this is a testing release and I am testing, I run Jaunty on my primary system and I was able to find some info for that version to get things running, but as I will move to Koala permanently once it is released and if my test goes well I will continue to test and likely move on my primary system (I can afford some issues and bugs..)  

Can someone let me know the "proper" method to install these items, which packages to install, is there a correct order, and if possible I have been searching to find out what codecs play which types of media.  IE:  MP3, Windows Media, etc...I haven't found a list, I have found that most people install ubuntu-restricted-extras and then a codecs package, but I haven't found that for Koala yet, which repos to add, and then for Adobe I tried doing an install using sudo apt-get install flashplugin-nonfree but went to a page and got an error that I needed a new/updated version of adobe flash as well as it was not working properly.

Thanks!
Virtual Jake

---

### Post by virtualu2 on 2009-09-28
Sorry, On more quick one, I also really like Opera, and every distro I have tried I have found that opera is slow over wireless, wired connections are fine, but wireless is terrible, sometimes wired is also bad, I can't figure it out and have posted in a few forums and I haven't gotten any replies that have worked.....

I have to install the Citrix plugin as well, is that OK to do in Koala just installing the linux client for citrix as well as copying the cert keys?  

The laptop is a 4gb Dell E6500, Dual Core Intel 64bit/32bit (Some people ask if it is strictly a 64bit processor - I haven't seen one as 32bit always has worked and I am running 32bit koala as I have had issues with 3rd party apps such as the citrix plugin on 64bit in the past).....

---

### Post by joey-elijah on 2009-09-28
Two very simple ways

sudo apt-get install ubuntu-restricted-extras

This installs flash, java, etc

A more through way is to use Ubuntu Tweak and install the 'mediabuntu' packages which comes with everything (including the proverbial kitchen sink). 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by barrieluv on 2009-09-29
For Tweetdeck, go to the website and click the "Download now, it's free" button.

---

### Post by gnomeuser on 2009-09-29
When you attempt to play a currently unsupported filetype in something like totem it should offer to search the repos for packages that grant you support. If this does not happen your best bet is to install the gstreamer-ffmpeg and the gstreamer-plugins-(ugly/good) in both the regular and the multiverse versions. This will install sufficient media support to play pretty much anything.

Now you must realize that if the law where you live acknowledge software patents installing these packages without a patent license from the patent holder.. will put you in violation of the law and subject to litigation. This is also why Ubuntu does not ship this support by default, we would be liable for something called Contributory Patent Infringement, which I assure you are 3 very expensive words.

The alternative is paying for support, [Fluendo](http://www.fluendo.com/) has an excellent licensed codec pack with a support solution. It's proprietary solution and will cost you a bit of money but they are high quality and the money you spend on this goes to a company that fuels development of the gstreamer framework and open formats as well as open media interaction programs such as moovida. 

As for flash, installing the flash-installer package followed by restarting the browser should work, if it does not please file a bug (the easiest way is to run 'ubuntu-bug flash-installer' from the commandline which will collect all the correct data). If it does not work, it is a bug and should be fixed. While we cannot fix flash itself since adobe will not let us, we can fix problems where your browser doesn't correctly register the plugin which can happen.

---

### Post by VMC on 2009-09-29
> **virtualu2 said:**
> I am trying to find out the best method to install the codecs, restricted extras, Sun Java plugin, Mplayer for Mozilla, Adobe Flash, Adobe Air, and TweetDeck on Ubuntu 32bit Koala.Read the "[Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")". It works for karmic as well.

---

### Post by virtualu2 on 2009-09-29
Hi,
I added the repos below, as per the link listed below as well.  Do I still enable the Partner repo for adobe flash, acroreader, and other items?  How about Opera, and should I add the "backports" repo as per the web page listed below as well?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[B]sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Then I ran:  [/B]
    
 			  	 	 	 	 		 		 			**[COLOR=DarkRed]32-Bit Ubuntu Users:[/COLOR]**
 [B]sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
:popcorn:
[/B]

---

### Post by wnelson on 2009-09-29
This has helped me out a bunch.
[http://ubuntuforums.org/showthread.php?t=1181327&highlight=ubuntu+desktop](http://ubuntuforums.org/showthread.php?t=1181327&highlight=ubuntu+desktop)

---

### Post by meborc on 2009-09-30
[www.ubuntuguide.org](www.ubuntuguide.org) should also soon make a karmic version...

---

### Post by ranch hand on 2009-09-30
> **meborc said:**
> [www.ubuntuguide.org]("http://www.ubuntuguide.org") should also soon make a karmic version...
Been up for about a week.

---

### Post by tom56 on 2009-10-02
If I go to a page which requires flash it offers to install the missing plugins, but when I click it it says that there aren't any plugins available. Does anyone know what's going on? This used to work.

A good site to test this on is [http://www.guardian.co.uk/politics/video/2009/oct/01/labour-party-harriet-harman](http://www.guardian.co.uk/politics/video/2009/oct/01/labour-party-harriet-harman)

---

### Post by ranch hand on 2009-10-02
Go to

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

and add the medibuntu repo to your sources list (you will need to change the jaunty to karmic - their page is not fully edited for karmic yet).  Get the public key (all this is on that site - there is an index at the top of the page).

Run "sudo apt-get update"  and then "sudo apt-get install ubuntu-restricted-extras".  This ought to take care of that.  It will also have you hooked up with the source for those restricted things that those pop-ups refer to.  Restricted extras should install flash and java.

---

