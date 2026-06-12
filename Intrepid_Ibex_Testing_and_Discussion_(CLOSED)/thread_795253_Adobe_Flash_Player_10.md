---
title: "Adobe Flash Player 10"
date: 2008-05-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by omha on 2008-05-15
hey i just installed abobe flash player 10, and i really liked it, games run much faster and it seems to be very stable, atleast firefox hasnt crashed yet :)

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

anybody else tried it?

---

### Post by plun on 2008-05-15
Yup, better then Flash 9 and no random crashes.

I had libflashsupport installed and it gave crashes.

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport
```

Then install Flash 10


Pulseaudio and gstreamer was also updated today for Intrepid.


Also tested wih Adblock Plus turned off on a "crazy ads site" on one tab
and playing YouTube within another tab, rather high CPU.


Much better anyway and with Adblock PLus running, "nema problema"  :)

---

### Post by aamukahvi on 2008-05-15
[http://labs.adobe.com/technologies/flashplayer10/releasenotes.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes.html)
It lists Ubuntu support as one of the enhancements. What does that mean?

---

### Post by nikopol on 2008-05-15
> **aamukahvi said:**
> [http://labs.adobe.com/technologies/flashplayer10/releasenotes.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes.html)
It lists Ubuntu support as one of the enhancements. What does that mean?

They are considering Ubuntu support to be a basic essential as it is now a major OS. IIRC they are now releasing Linux, Windows and OSX updates simultaneously which is also good news.

(and yes before some pedant points out, it isn't good news as it's non free software, gnash should be preferred etc etc etc)

---

### Post by plun on 2008-05-15
Some more facts about Adobes Flash from Phoronix

[http://www.phoronix.com/scan.php?page=news_item&px=NjQ3Nw](http://www.phoronix.com/scan.php?page=news_item&px=NjQ3Nw)


Adobe also earlier joined Linux Foundation
[http://linux-foundation.org/weblogs/press/2008/03/30/adobe-joins-linux-foundation-with-focus-on-linux-for-web-20-applications/](http://linux-foundation.org/weblogs/press/2008/03/30/adobe-joins-linux-foundation-with-focus-on-linux-for-web-20-applications/)

---

### Post by ouff on 2008-05-15
I just installed Flash Player 10 and went to my default flash test site, toyota.com.  It still is messed up with version 10.  There is a big white box in the middle of the site and all the pop-down menus render behind it.  Is this a settings problem?  A Toyota site compliance problem?  Settings problem?  What is up with this?  Why does no one seem to care?

It's not that I want to go to the Toyota site every day, but I'd like web sites that make heavy use of flash to render properly, and most of them in Linux don't.  In fact, anything beyond a flash movie player or other single panel of flash content doesn't work well with the Linux plugin.

Any thoughts?

---

### Post by | MM | on 2008-05-15
Works well with Opera 64bit on Hardy x86_64.  Still some old bugs like Flash rendering above other parts of the webpage, such as dropdown menus.  Hopefully this will change...

---

### Post by damoxc on 2008-05-16
If you leave libflashsupport installed on hardy it seems to play nice, both with not crashing firefox and being able to play sound at the same time as other applications.

---

### Post by plun on 2008-05-16
> **damoxc said:**
> If you leave libflashsupport installed on hardy it seems to play nice, both with not crashing firefox and being able to play sound at the same time as other applications.

Well...  Intrepid Ibex Development

Libflashsupport was discussed during Hardys development and I have had it installed also with Intrepids repo

But FF3 crashed after Adobe Beta install yesterday.  Running **FF3pre**

Pulseaudio and gstreamer was also updated yesterday.

After liblashsupport removal everything was OK and "rock solid".


So its maybe more important with "crazy" Intrepid users opinions...:) 
(within this group)

---

### Post by yaknowwat on 2008-05-16
yeah there seems to be some good improvements in this release I hope to see Flash Transparency before the final release though.

---

### Post by steeleyuk on 2008-05-16
> Is this a settings problem? A Toyota site compliance problem? Settings problem? What is up with this? Why does no one seem to care?

Getting same problem here with other sites, can't see it being a settings problem. Always been fine in Windows though, just no sign of a fix at the moment.

---

### Post by macaholic on 2008-05-16
I tried using nspluginwrapper to install it, but that didn't work, how do you install it on 64-bit?

---

### Post by plun on 2008-05-16
> **steeleyuk said:**
> Getting same problem here with other sites, can't see it being a settings problem. Always been fine in Windows though, just no sign of a fix at the moment.

Ask within Adobes forum, its still their proprietary code so the Linux world cannot fix anything.

[http://www.adobe.com/cfusion/webforums/forum/categories.cfm?forumid=72&catid=675](http://www.adobe.com/cfusion/webforums/forum/categories.cfm?forumid=72&catid=675)

---

### Post by steeleyuk on 2008-05-16
I know its an Adobe bug, I'm not blaming anybody from the open source world. Its been reported many times, been around for a long time and there are many posts and sites which can be found via Google talking about this issue.

---

### Post by Pr0zAck on 2008-05-16
Hey I just installed Flash Player 10 and Firefox does not crash every time i open a web page that has flash on it anymore.

---

### Post by Gourgi on 2008-05-18
amd64 here 
i downloaded and extracted the tar.gz

```
sudo ./flashplayer-installer 

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
```
:-k

any help?
thanks in advance

[COLOR="Red"]EDIT:[/COLOR]
i 've installed it :D
[http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/](http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/)

---

### Post by meborc on 2008-05-18
toyota.com displays without a problem... although [www.ubuntuguide.org](www.ubuntuguide.org) restarts my X session (forgot to mention that i have yet not moved to flash player 10)

---

### Post by MaX on 2008-05-19
It's kind of funny how they say they support Ubuntu but they only have .rpm and .tar.gz files...

---

### Post by odinfromvalhalla on 2008-05-20
> **macaholic said:**
> I tried using nspluginwrapper to install it, but that didn't work, how do you install it on 64-bit?

Follow my tutorial or just run this [script]("http://www.myscienceisbetter.info/projects/install_flash_player_10_ubuntu64bit") to [install flash player 10 on Ubuntu Hardy 64bit]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

---

### Post by mgm2rr on 2008-05-20
I know its beta, but if you have had trouble with shaky, unstable video on the web, this player may totally fix it.  I have an old Dell with a P4 processor and a 64mb NVidia GeForce card, and I never got good playback on Youtube until yesterday when I added Flash Player 10.

---

### Post by ronacc on 2008-05-20
Works good for me with FF3 on hardy 64bit following Odins tutorial , Trying now to get it to work with Opera 64bit . so far Opera sees it as a plugin but won't use it.

EDIT  opps my bad , forgot I had plugins turned off in Opera . turned them on and flash 10 works fine in opera .

---

### Post by odinfromvalhalla on 2008-05-20
> **ronacc said:**
> Works good for me with FF3 on hardy 64bit following Odins tutorial , Trying now to get it to work with Opera 64bit . so far Opera sees it as a plugin but won't use it.

I have installed opera from [ftp://ftp.iasi.roedu.net/mirrors/ftp.opera.com/linux/950b2/final/en/x86_64/](ftp://ftp.iasi.roedu.net/mirrors/ftp.opera.com/linux/950b2/final/en/x86_64/) on both my PC and my notebook and on first run Opera just detected the plugin and it works.

---

### Post by ronacc on 2008-05-20
I must have added my edit at the same time you replied .

---

### Post by caryb on 2008-05-20
It just landed in the repo's & installed on my 64bit PC, seems to work great:)


Cary

---

### Post by syxbit on 2008-05-23
this is great news.
i was always so annoyed at how a stable LTS ubuntu release wouldn't even let me watch youtube videos. how on earth can (despite it maybe not being entirely ubuntu's fault) an OS ever be considered a competitor to Windows or Mac, if you can't even browse the web!

i'm gonna try it out with a fresh hardy x64 tonight!

---

### Post by hauj0bb on 2008-05-24
> **| MM | said:**
> Works well with Opera 64bit on Hardy x86_64.  Still some old bugs like Flash rendering above other parts of the webpage, such as dropdown menus.  Hopefully this will change...

How did you manage to get this installed on hardy x86_64? I can't seem create a *.deb package using alien due to a architecture complaint, and the tarball package complains about architecture as well.

I even went as far as editing the flash 10 source code to ignore the cpu error, but it didn't work after its supposed successful install. I also tried moving the *.so files to the proper directories, and yet again it didn't work.

any insight would be awesome, or even better yet.. if someone here running i386 arch would create a deb package using alien, and post it. I then could force arch with dpkg.

I'm using Firefox 3 b5 on AMD64 hardy.

> **caryb said:**
> It just landed in the repo's & installed on my 64bit PC, seems to work great:)


Cary

What repo are you seeing this release in?


Edit: Fixed my issue by reading, DUH. :(

---

### Post by HotShotDJ on 2008-05-24
> **ouff said:**
> There is a big white box in the middle of the site and all the pop-down menus render behind it.  Is this a settings problem? Until this problem is fixed, Flash will remain irrelevant on Linux.  First, Adobe blamed FireFox developers... FireFox developers FIXED the problem Adobe complained about.  New version of Flash STILL doesn't work properly.  Bah.  Sounds like a lot of lip service from Adobe and absolutely NO action.

---

### Post by meborc on 2008-05-24
well... if gnash would get more love ;) ... it now already supports youtube AND youtube new player... 

gnash developer interview form UDS - [http://www.youtube.com/watch?v=zoNvsiBTQDE](http://www.youtube.com/watch?v=zoNvsiBTQDE)

---

### Post by peacewarrior on 2008-05-24
I just tried installing the flash plugin from adobe, and it tells me I don't have the proper permissions, what do I do?

---

### Post by meborc on 2008-05-24
> **peacewarrior said:**
> I just tried installing the flash plugin from adobe, and it tells me I don't have the proper permissions, what do I do?

how did you install it? i mean, if you install in into /usr/somewhere then you need to use sudo... if you install it into your home folder, then you don't need to have superuser permissions

---

### Post by Gina on 2008-05-24
Do it as root ie. sudo in the terminal.

Edit... meborc beat me to it :lolflag:

---

### Post by peacewarrior on 2008-05-24
Okay putting it in the home folder works, and I understand why. Now its telling me to ask my admin to remove xpti.dat, How do I do that?

---

### Post by peacewarrior on 2008-05-24
I mean how as admin of my own computer do I remove xpti.dat so the my plugin will complete the install?

---

### Post by plun on 2008-05-24
First uninstall, then install

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport
```

Gnash and swfdec is just an extra uninstall if your install is messed up.

(some users needs libflashsupport, just to reinstall if no sound)


Install Flash 10


Enjoy **real HD streaming** which nearly all TV stations now sends out..:)   (YouTube is a low quality service)

:)

---

### Post by Trueno22 on 2008-05-24
tried to install it it works in youtube just fine but on espn.com it shows up as I don't have flash installed.  Weird.

---

### Post by plun on 2008-05-24
> **Trueno22 said:**
> tried to install it it works in youtube just fine but on espn.com it shows up as I don't have flash installed.  Weird.

Well... it can be so easy that you must restart Firefox.

With   **about:plugins**   within the URL adress bar you can check what
Firefox sees as installed plugins.

Then its a big difference between low quality You Tube movies and
HD streamed first class movies.

This thread is important for this.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


"someone" choose d wrong solution for 99% of all media....:)

---

### Post by andrek on 2008-05-24
> **plun said:**
> 

Enjoy **real HD streaming** which nearly all TV stations now sends out..:)   (YouTube is a low quality service)

:)
What are you talking about? Link please ;)

---

### Post by plun on 2008-05-24
> **andrek said:**
> What are you talking about? Link please ;)

Well, Poland ?

Swedish State Television sends out HD formats,  H.264.

I don't now the situation within your country.


Some other "home brewed players" cannot manage HD streams   :)

Maybe a problem for some users or "self punishers"..:confused:

YouTube uses "low quality" streams.

---

### Post by syxbit on 2008-05-24
was easy to get working.
seems better than the repo v9.
it's still not perfect.
the espn site doesn't really work. but youtube, and other stuff seems much improved. and it doesn't break my rhythmbox :)
finally!
thanks guys

---

### Post by ronacc on 2008-05-24
> **plun said:**
> Well, Poland ?

Swedish State Television sends out HD formats,  H.264.

I don't now the situation within your country.


.

alot of stations here in the USA are going to Silverlight . :(

---

### Post by peacewarrior on 2008-05-25
when I try the apt-get purge command for my flash players and when I check add/remove, they both tell me that the flash players are uninstalled. but when I try to play a flash video it still brings up the players that are supposed to be uninstalled.
How can I fix this.

---

### Post by meborc on 2008-05-25
you probably didn't install them from the repos but compiled them yourself... if so then there should be a uninstall script in the program folder... or you can just remove the folder :)

---

### Post by Trueno22 on 2008-05-25
> **syxbit said:**
> was easy to get working.
seems better than the repo v9.
it's still not perfect.
the espn site doesn't really work. but youtube, and other stuff seems much improved. and it doesn't break my rhythmbox :)
finally!
thanks guys

yup it doesn't work with the video on the main page elsewhere on the site is fine though.

---

### Post by covert215 on 2008-05-26
I'm guessing that the issues with ESPN's website are their own fault.  They attempt to detect the version of your flash player and I guess 10 doesn't match what they are looking for.

---

### Post by cybergalvez on 2008-05-26
> **odinfromvalhalla said:**
> Follow my tutorial or just run this [script]("http://www.myscienceisbetter.info/projects/install_flash_player_10_ubuntu64bit") to [install flash player 10 on Ubuntu Hardy 64bit]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

I had tried this script and it wored for FF, but not for my screenlets, so I tried a different approach, I just replaced what I needed for the official install.  Here is the python script that I wrote to automate this:

```

#!/usr/bin/env python
import os, sys, subprocess

# this installs some new version of flash over the original one
# you should have already installed flash with apt-get install flashplugin-nonfree
# this will download 
# http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
# if you want it to otherwise download the file yourself from
# http://labs.adobe.com/downloads/flashplayer10.html

# edit these variable is needed
download_url = 'http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz'
flash_gz = 'flashplayer10_install_linux_051508.tar.gz'
flash_10_folder = 'install_flash_player_10_linux'
flash_so = 'libflashplayer.so'
md5 = '243dec36ba455c72beb909025c36e996 *flashplayer10_install_linux_051508.tar.gz'


def message():
    # prints our message
    msg = '''
    The intent of this script is to install some new version of flash over the 
    exsisting flahplugin-nonfree in Hardy
    you need to have already installed flashplugin-nonfree
    
    usage 
    install:  
    \tinstall_new_flash_over_official_flash <<newflash.tar.gz>> or
    \tinstall_new_flash_over_official_flash -i
    download and install:
    \tinstall_new_flash_over_official_flash -w
    remove "other" flash plugins 
    \tinstall_new_flash_over_official_flash -c
    deep clean removes and reinstalls flashnonfree and nspwrapper
    \tinstall_new_flash_over_official_flash -d
    uninstall and restore the normal flash
    \tinstall_new_flash_over_official_flash -u
    
    '''
    print msg
    
def download():
    # downloads flash for us
    download_cmd = 'wget %s' % download_url
    subprocess.call(download_cmd, shell=True)
    m = subprocess.Popen(['md5sum', '-c', '-'], stdin=subprocess.PIPE, stdout=subprocess.PIPE)
    results = m.communicate(input=md5)[0].strip()
    print 'md5 check: %s' % results
    if not results.endswith('OK'):
        print 'download failed try again'
        sys.exit()

def install_flash(flash=None):
    # installs the new flash plugin for us
    if not flash:
        flash = sys.argv[1]
    
    untar_cmd = 'tar zxvf %s' % flash
    copy_flash_cmd = 'sudo cp %s /usr/lib/flashplugin-nonfree/' % flash_so
    nspwrapper_cmd = 'export NSPLUGIN_DIR=/var/lib/flashplugin-nonfree/; \
    nspluginwrapper -n -i /usr/lib/flashplugin-nonfree/%s' % flash_so
    
    #untar
    subprocess.call(untar_cmd, shell=True)
    
    os.chdir(flash_10_folder)
    
    # copy flash to the right spot
    subprocess.call(copy_flash_cmd, shell=True)
    
    # make the nspwrapper
    subprocess.call(nspwrapper_cmd, shell=True)

def cleanup():
    # gets rid of some other flash plugsins
    cleanup_cmd = 'sudo apt-get remove -y --purge \
    gnash gnash-common \
    mozilla-plugin-gnash \
    swfdec-mozilla \
    libflashsupport'
    print '''
    removing:
    gnash gnash-common
    mozilla-plugin-gnash
    swfdec-mozilla
    libflashsupport
    '''
    subprocess.call(cleanup_cmd, shell=True)
    
def deep_clean():
    # either uninstalls what we've done or simply makes sure that we really have
    # the nonfreeflash installed
    
    remove_cmd = 'sudo apt-get remove -y --purge flashplugin-nonfree nspluginwrapper'
    reinstall_cmd = 'sudo apt-get install flashplugin-nonfree'
    
    # kill add browsers
    subprocess.call('sudo killall -9 firefox', shell=True)
    
    #remove flash first
    subprocess.call(remove_cmd, shell=True)
    
    #install flash again
    subprocess.call(reinstall_cmd, shell=True)
    
    # done print a message
    print 'flash should be reinstalled open your browser and test'

if __name__ == '__main__':
    if not len(sys.argv)>1:
        message()
        sys.exit()
    elif sys.argv[1].lower() == '-c':
        cleanup()
    elif sys.argv[1].lower() in ['-d', '-u']:
        deep_clean()
    elif sys.argv[1].lower() == '-w':
        download()
        install_flash(flash_gz)
    elif ((sys.argv[1].lower() == '-i') and 
    (os.path.exists(flash_gz))):
        install_flash(flash_gz)
    elif os.path.exists(sys.argv[1]):
        install_flash()
    else:
        print '\n%s does not exsist or the parameter is wrong please try again' % sys.argv[1]
        message()
        sys.exit()
        


```

---

### Post by aikishugyo on 2008-05-26
> **mgm2rr said:**
> I know its beta, but if you have had trouble with shaky, unstable video on the web, this player may totally fix it.  I have an old Dell with a P4 processor and a 64mb NVidia GeForce card, and I never got good playback on Youtube until yesterday when I added Flash Player 10.

That's a shame, but I would not put the blame on flashplayer. Perhaps you simply had too many processes and services (daemons?) running. My wife uses an old Toshiba laptop with a 500 MHz Celeron, 384 MiB of RAM, and runs Debian unstable on it with great video playback.

---

### Post by BDNiner on 2008-07-03
I got it installed and there are still some minor issues but definately a step in the correct direction. I like that menu overlays are no longer stuck behind other flash boxes. Now i can browse cnnsi.com without any issues. i am going to try all the sites that i still keep my windows computer around for.

And they fixed the mouse wheel scroll over flash windows, that was the second most annoying bug for me.

---

### Post by cicoandcico on 2008-07-03
the mouse scroll was fixed by firefox developers, not by adobe! :)

---

### Post by plun on 2008-07-03
New features for Beta 2

[http://labs.adobe.com/technologies/flashplayer10/releasenotes.html#features](http://labs.adobe.com/technologies/flashplayer10/releasenotes.html#features)

And its within Intrepids repo, have not checked this version

[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/002906.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/002906.html)

---

### Post by freddybob on 2008-07-03
With Flash 10 beta 2 installed Firefox crashes whenever I try to access [www.bbc.co.uk](www.bbc.co.uk) - this was not a problem with the first beta.

Pity because I was looking forward to seeing transparency finally working (the clock on the BBC's homepage should not have a black background).

Does anyone else have this problem?

---

### Post by t.alex on 2008-07-03
some problem here. this second beta looks really bad

---

### Post by plun on 2008-07-03
> **t.alex said:**
> some problem here. this second beta looks really bad

Well... its terrible for high quality Flash streams...:(

Example from Swedish public televison

[http://playrapport.se](http://playrapport.se)


YouTubes lower quality works better but not good, cracklings sometimes..

---

### Post by olskar on 2008-07-03
> **plun said:**
> Well... its terrible for high quality Flash streams...:(

Example from Swedish public televison

[http://playrapport.se](http://playrapport.se)


YouTubes lower quality works better but not good, cracklings sometimes..

Is it even worse than with the first beta?

---

### Post by cariboo on 2008-07-04
I had a look, earlier this afternoon and it didn't look to bad at all, mind you I didn't run it full screen. A curious thing I found, is that it looked like it was streaming from a Canadian server. That is pretty cool seeing as the major TV station on the west coast doesn't have a high def feed yet.

Jim

---

### Post by plun on 2008-07-04
> **olskar said:**
> Is it even worse than with the first beta?

Well, Beta 1 works much better but apparently we have "full house" with
sound bugs....:)

[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

I also dont remember if Firefox should use the Alsa plugin or Pulseaudio  ?

Most important is that all tests are done with high def streams an not YouTubes "crap".

---

### Post by volanin on 2008-07-04
Just to make sure...
Can someone access [www.dilbert.com](www.dilbert.com) ?
It crashes on me everytime.
:(

---

### Post by NilsE on 2008-07-04
> **volanin said:**
> Just to make sure...
Can someone access [www.dilbert.com](www.dilbert.com) ?
It crashes on me everytime.
:(Does the same in Hardy.  First site I came across that crashes with version 10

---

### Post by silkstone on 2008-07-04
I've just tried the Dilbert site, including the animated cartoon, and have not had a problem. (Using Hardy.)

In case it helps, I'm using...

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 b218

... installed using the procedure on Troubleshooting Adobe Flash near the end of this guide...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I also uninstalled libflashsupport from Synaptic.

---

### Post by volanin on 2008-07-04
> **silkstone said:**
> In case it helps, I'm using...
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 b218

You are probably using the old beta!
The newly released beta is this:

    File name: libflashplayer.so
    Shockwave Flash 10.0.0 d525

---

### Post by silkstone on 2008-07-04
Ah, that would explain it. In that case I'll keep what I have. :)

---

### Post by dangmc on 2008-07-05
bug report: just installed flash 10 beta 2 plugin for firefox/swiftweasel. Firefox/Swiftweasel 3 crash when going to full screen view-streaming video (hulu.com), Swiftweasel 2.0.0.14 runs perfectly! I'm using dual boot 8.04/winXP pro w/homebuilt  Abit is7,p42.8g, 3g pc3200.                                               Warning: Error in parsing value for property 'filter'.  Declaration dropped.
Source File: [http://static.hulu.com/stylesheets/hulu_10729.css](http://static.hulu.com/stylesheets/hulu_10729.css)
Line: 1

---

### Post by merlyn on 2008-07-06
I've noticed a few odd things with Flash 9.x and the current FF 3.0 beta offering.

As a WoW player I visit the official site regularly, where the various flash elements are displayed with a black "box" surrounding them.

So off I went and installed Flash 10 to see if things would improve.

Unfortunately the flash elements did not display on the WoW official site at all.

Another odd thing that occurred was that when I visited the new Diablo 3 site. All the flash elements were displayed correctly, running much smoother and faster.

However, each time I attempted to scroll to the bottom of the page, to view more content the browser crashed each time.

To date I have yet to successfully view YouTube video with either version.

Unless anyone has some suggestions, it's back to 9.x for now.

Cheers.

---

### Post by isaacj87 on 2008-07-06
Hey everyone,

I'm a little late to this thread, but I can sense that many users are unhappy with the second beta (d525). There was definite decline in performance and firefox crashed so many times, I almost pulled my hair out. In any case, I went on a search to find the first beta (b218 ), as it worked fairly well with Hardy, Firefox 3.0, and PulseAudio (after a little [tweaking]("http://ubuntuforums.org/showthread.php?t=789578") of course ;)). I apologize if this is a dupe, but you can get the first beta by running this command:

```
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
```

I hope that's helpful. I also hope that Adobe works a miracle for the next beta release, cause beta 2 didn't cut it for me. :(

---

### Post by plun on 2008-07-06
> **isaacj87 said:**
> 

I hope that's helpful. I also hope that Adobe works a miracle for the next beta release, cause beta 2 didn't cut it for me. :(

Well, I downloaded my Beta 1 from Intrepids repo before it was removed,


Reference sites with broken flash ( at least for me)

BBC
[http://news.bbc.co.uk/2/hi/americas/7486712.stm](http://news.bbc.co.uk/2/hi/americas/7486712.stm)

CNN
[http://edition.cnn.com](http://edition.cnn.com)


BBC also got a **akamai stream** stop-error for mplayer, forget about **Olympic Games** and Ubuntu maybe...:(    

Maybe a -playlist solves akamai errors.:confused:

Low-Quality streams works such as You Tube.

---

### Post by psyke83 on 2008-07-06
> **plun said:**
> Well, I downloaded my Beta 1 from Intrepids repo before it was removed,


Reference sites with broken flash ( at least for me)

BBC
[http://news.bbc.co.uk/2/hi/americas/7486712.stm](http://news.bbc.co.uk/2/hi/americas/7486712.stm)

CNN
[http://edition.cnn.com](http://edition.cnn.com)


BBC also got a **akamai stream** stop-error for mplayer, forget about **Olympic Games** and Ubuntu maybe...:(    

Maybe a -playlist solves akamai errors.:confused:

Low-Quality streams works such as You Tube.

I've updated my guide to provide links to debs for beta 1 and 2 of Flash v10. If you check Part B of the guide, you can find the proper links if you look carefully. Before anyone tries, note that the rest of this guide is *not* for Intrepid (as several steps are redundant) and it doesn't anticipate Intrepid kernel bugs.

It's better to use the packages rather than manually installing the plugin.

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by Umar07 on 2008-07-06
i installed the new flash for firefox and my youtube and google videos did not work i need some help guys

---

### Post by spamzilla on 2008-07-06
> **Umar07 said:**
> i installed the new flash for firefox and my youtube and google videos did not work i need some help guys

I had the same problem. Reinstalling the repo version of flash 10 using Synaptics fixed the problem.

---

### Post by highlyevolved on 2008-07-08
How do I completely uninstall flash 10?

---

### Post by Nullack on 2008-07-08
synaptic or apt-get remove

---

### Post by highlyevolved on 2008-07-08
> **Nullack said:**
> synaptic or apt-get remove


I can't find "libflashplayer.so" anywhere in the mozilla folders, even after I do a search and it doesn't come up in Synaptic..

---

### Post by xebian on 2008-07-08
> **plun said:**
> Well, I downloaded my Beta 1 from Intrepids repo before it was removed,



Ubuntu can't redistribute flash binaries.

---

### Post by plun on 2008-07-08
> **xebian said:**
> Ubuntu can't redistribute flash binaries.

OK.. lets define the file as a "wrapper" then...:)

Nevertheless its just to read psyke83s thread and use
the wrapper file for Beta 1 to download from Adobe. 

"Nema problema" except "state of the art" for web multimedia and Linux..

The world is indeed commercial filled with protected stuff ...:KS

---

### Post by NilsE on 2008-07-08
> **isaacj87 said:**
> 

```
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
```

I hope that's helpful. 
Thanks.  That reminded me that I still had 10-B1 so I reinstalled it and solved my problems. In my opinion 10-B1 is still much better than version 9 since it is faster, cleaner and solved the menu behind the video problem. 

The only real problem I was having with 10-B2 was with certain sites crashing FF3. [www.audible.com](www.audible.com) was one of the sites that would crash 10-B2 when it was opened and 10-B1 works fine.

---

### Post by jerrylamos on 2008-07-09
Flash player from synaptic Xubuntu-restricted-extras works fine with BBC News on Gutsy and Hardy, not with Ibis Alpha.  BBC says it can't work with the level of flash player on Ibis Alpha.  ?

Jerry

---

### Post by fluteflute on 2008-07-11
This is in hardy-backports now. I hope its stable enough! :)

---

### Post by chemist109 on 2008-07-11
It's definitely not stable enough!  I've had numerous crashes in FF3.  Took me a little while to remember that I updated the Flash plugin.  I'm back on version 9.

---

### Post by volanin on 2008-07-11
[QUOTE=fluteflute]This is in hardy-backports now. I hope its stable enough! :)[/QUOTE]

[QUOTE=chemist109]It's definitely not stable enough! I've had numerous crashes in FF3. Took me a little while to remember that I updated the Flash plugin. I'm back on version 9.[/QUOTE]

I definitely agree with chemist109.
The adobe flash plugin crashes in many common websites.

**If you know of any website that crashes with the new plugin, please post it in this bug report:**
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247721](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247721)

---

### Post by clw3388 on 2008-07-11
well i am still running version 9.0.124.0 .. Call me strange but i like stable, no beta fir me... Runs youtube great:)!!? Haven't tried it on other sites that i know of...

---

### Post by scradock on 2008-07-11
> **volanin said:**
> I definitely agree with chemist109.
The adobe flash plugin crashes in many common websites.

**If you know of any website that crashes with the new plugin, please post it in this bug report:**
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247721](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247721)

The only site listed so far in the launchpad bug report is the Dilbert cartoon site, which works perfectly for me with the latest flashplugin-nonfree 10.0.1.218+10.0.0.525ubuntu1 in Intrepid with Firefox 3.0

---

### Post by psyke83 on 2008-07-11
> **scradock said:**
> The only site listed so far in the launchpad bug report is the Dilbert cartoon site, which works perfectly for me with the latest flashplugin-nonfree 10.0.1.218+10.0.0.525ubuntu1 in Intrepid with Firefox 3.0

That's because you're using Ubuntu 64bit, which has nspluginwrapper installed by default. This bug will only affect 32bit users.

> **volanin said:**
> If you know of any website that crashes with the new plugin, please post it in this bug report:
[https://bugs.launchpad.net/ubuntu/+s...ee/+bug/247721](https://bugs.launchpad.net/ubuntu/+s...ee/+bug/247721)

Try searching before reporting a new bug, as somebody already filed a bug before yours. I marked your (newer) bug as a duplicate of this one, and added some more details: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247682](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247682)

I have created a new thread to propose a workaround for these crashes. **Please test and reply to my workaround in the following thread**: [http://ubuntuforums.org/showthread.php?p=5367471](http://ubuntuforums.org/showthread.php?p=5367471)

---

### Post by xebian on 2008-07-11
> **psyke83 said:**
> That's because you're using Ubuntu 64bit, which has nspluginwrapper installed by default. This bug will only affect 32bit users.



Try searching before reporting a new bug, as somebody already filed a bug before yours. I marked your (newer) bug as a duplicate of this one, and added some more details: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247682](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247682)

I have created a new thread to propose a workaround for these crashes. **Please test and reply to my workaround in this thread**: [http://ubuntuforums.org/showthread.php?p=5367471](http://ubuntuforums.org/showthread.php?p=5367471)

Why is nspluginwrapper now necessary for 32bits?  It's required for 64bit bec the flash plugin binary is 32bit AFAIK.

---

### Post by psyke83 on 2008-07-11
> **xebian said:**
> Why is nspluginwrapper now necessary for 32bits?  It's required for 64bit bec the flash plugin binary is 32bit AFAIK.

I replied to you in the other thread (it's necessary, as I linked that thread to the bug report). If you've any other comments or questions re: nspluginwrapper, please reply in that thread in future.

---

### Post by jerrylamos on 2008-07-11
> **jerrylamos said:**
> Flash player from synaptic Xubuntu-restricted-extras works fine with BBC News on Gutsy and Hardy, not with Ibis Alpha.  BBC says it can't work with the level of flash player on Ibis Alpha.  ?

Jerry

Firefox-2 from synaptic plus Xubuntu-restricted-extras FlashPlayer work on Ibex Alpha 1 on BBC, YouTube, ....

Firefox 3 with Xubuntu-restricted-extras FlashPlayer crashes Firefox when going to You Tube, so much so that Ibex Alpha 1 is crippled and must be battered into restart.  Note this is an old Dell triple booted with Xubuntu Hardy and Gutsy, both of which work with Firefox 3.

Wonder what Alpha 2 will do.

Jerry

---

### Post by volanin on 2008-07-11
> **psyke83 said:**
> Try searching before reporting a new bug, as somebody already filed a bug before yours. I marked your (newer) bug as a duplicate of this one, and added some more details: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247682](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247682)

I always search!
This one passed me by... thanks for the duplicate mark!


> **psyke83 said:**
> I have created a new thread to propose a workaround for these crashes. **Please test and reply to my workaround in the following thread**: [http://ubuntuforums.org/showthread.php?p=5367471](http://ubuntuforums.org/showthread.php?p=5367471)

Nspluginwrapper solution = perfect!
Thank you a lot psyke83!
:)

---

### Post by kbozen on 2008-07-13
the last ubuntu update (with backports) solved the problem; it updated:

- firefox-3.0
(3.0.1+build1+nobinonly-0ubuntu0.8.04.1) hardy-proposed

- flashplugin-nonfree
(10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) hardy-backports

---

### Post by pcjunkie on 2008-07-13
> **nikopol said:**
> They are considering Ubuntu support to be a basic essential as it is now a major OS. IIRC they are now releasing Linux, Windows and OSX updates simultaneously which is also good news.

(and yes before some pedant points out, it isn't good news as it's non free software, gnash should be preferred etc etc etc)


Does this mean we can expect a Photoshop Native port and full PS menu access along with other Adobe apps...

As a Multimedia webby guy both PS and Dreamweaver are my fave~! 
Wine is ok but better on XP without Virtual machining it. It would be good to use both Gimp (Has advantages) and PS (has familiarity and more tools) together.

Anyways, flash on some pages eats my CPU rapidly. If a page has 3 or more flash apps running, the system slows down and CPU use increases to 100% eventually.

---

### Post by cjm5229 on 2008-07-13
I have Flashplayer 10 beta 2 in Intrepid and it is doing quite well except for the sound, it comes out of the computer speaker instead of going through the sound card. It also did it with the flash from the repo's (beta 1). I have an intel onboard soundcard.

---

### Post by psyke83 on 2008-07-13
> **cjm5229 said:**
> I have Flashplayer 10 beta 2 in Intrepid and it is doing quite well except for the sound, it comes out of the computer speaker instead of going through the sound card. It also did it with the flash from the repo's (beta 1). I have an intel onboard soundcard.

You need to blacklist the snd_pcsp kernel module to prevent PulseAudio from choosing the PC Speaker as a PCM device.

---

### Post by LiquidOC on 2008-07-14
I've been searching this forum for 2 days now trying to find the answer to this question, which someone asked earlier, but has never been answered. How do I uninstall the flash 10 beta 2 and reinstall the beta 1 or even flash 9?

---

### Post by NilsE on 2008-07-14
> **LiquidOC said:**
> I've been searching this forum for 2 days now trying to find the answer to this question, which someone asked earlier, but has never been answered. How do I uninstall the flash 10 beta 2 and reinstall the beta 1 or even flash 9?

In synaptic: remove flashplugin-nonfree

Search for libflashplayer.so and if you find any delete all of them (will need to be as root)

In synaptic: Install flashplugin-nonfree

You should now be back to version 9

---

### Post by LiquidOC on 2008-07-14
When I enter the command to remove "flashplugin-nonfree" i get this:

gaylan@gaylan-laptop:~$ sudo apt-get remove flashplugin-nonfree
[sudo] password for gaylan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


so that's not how I can uninstall it, when I search for flash in the synaptic package manager, nothing is checked, and I still have flash 10 installed.....

---

### Post by olskar on 2008-07-14
Perhaps it is installed manually?

Check in /home/<YOURUSERNAME>/.mozilla/plugins/

---

### Post by LiquidOC on 2008-07-14
I did install it from the command line, by downloading a tar.gz, but I cannot find the .mozilla folder, it is not in my /home/gaylan directory, at least.

---

### Post by olskar on 2008-07-14
What do you get if you put

> find / -name '*libflash*'


in the terminal?

---

### Post by NilsE on 2008-07-14
> **LiquidOC said:**
> 
so that's not how I can uninstall it, when I search for flash in the synaptic package manager, nothing is checked, and I still have flash 10 installed.....
That just proved that you installed it manually.  My suggestion to search for libflashplayer.so was meant to be outside of Synaptic using either find in a terminal or using the search tool under places.  If you find any delete them.

Then go back to Synaptic and install flashplugin-nonfree to install version 9.

---

### Post by LiquidOC on 2008-07-14
Found all the libflash files, deleted 'em, now I'm wondering where I can find a Flash 10 Beta 1, as it seems to have worked better than beta 2?

---

### Post by cjm5229 on 2008-07-14
Use a root file manager, look in .usr/lib/mozilla/plugins, delete libflashplayer.so. Check /home/username/.mozilla/plugins, and if it is there remove it also. I believe those are the only two folders it would install to.

@ psyke83 
Thank You, That fixed the problem, I noticed earlier today that it was doing that in everything that used Pulse Audio, just wasn't sure how to fix it till I came back here and saw your post. Thanks again.
Carl
__[]("http://ubuntuforums.org/member.php?u=50843")

---

### Post by cjm5229 on 2008-07-14
> **LiquidOC said:**
> Found all the libflash files, deleted 'em, now I'm wondering where I can find a Flash 10 Beta 1, as it seems to have worked better than beta 2?
  
I have a beta1 I can send you. PM with your email and I can get it on it's way.

---

### Post by psyke83 on 2008-07-14
Anyone that needs Flash 10 beta 1 can find the deb package (for i386 users) here: [http://launchpadlibrarian.net/14629821/flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb](http://launchpadlibrarian.net/14629821/flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb)

You will also need the actual Flash .tar.gz (which is no longer available from Adobe), so it's also available here: [http://ubuntuforums.org/showpost.php?p=5355344&postcount=339](http://ubuntuforums.org/showpost.php?p=5355344&postcount=339)

---

### Post by Matt26 on 2008-07-21
> **psyke83 said:**
> Anyone that needs Flash 10 beta 1 can find the deb package (for i386 users) here: [http://launchpadlibrarian.net/14629821/flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb](http://launchpadlibrarian.net/14629821/flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb)

You will also need the actual Flash .tar.gz (which is no longer available from Adobe), so it's also available here: [http://ubuntuforums.org/showpost.php?p=5355344&postcount=339](http://ubuntuforums.org/showpost.php?p=5355344&postcount=339)

i have tried installing the .deb package but i get an error status when the package opens stating:

**Error: Dependency is not satisfiable: libflashsupport/libasound2-plugins**

does anyone know where i can get the proper versions of these dependencies?

thanks.

---

### Post by psyke83 on 2008-07-22
> **Matt26 said:**
> i have tried installing the .deb package but i get an error status when the package opens stating:

**Error: Dependency is not satisfiable: libflashsupport/libasound2-plugins**

does anyone know where i can get the proper versions of these dependencies?

thanks.

Install libasound2-plugins before installing the deb.

---

### Post by Matt26 on 2008-07-22
> **psyke83 said:**
> Install libasound2-plugins before installing the deb.

is this package included in synaptic, as i'm not sure where to get it?  the deb package states that the libflashplayer is a dependency as well, so would i also need this?

---

### Post by psyke83 on 2008-07-22
> **Matt26 said:**
> is this package included in synaptic, as i'm not sure where to get it?  the deb package states that the libflashplayer is a dependency as well, so would i also need this?

No, I believe it's and/or - one is required, not both. The "libflashsupport" library causes instability, so don't install it.

```
$ sudo apt-get install libasound2-plugins
```

Then install the Flash 10 beta 1 deb.

---

### Post by Matt26 on 2008-07-22
> **psyke83 said:**
> No, I believe it's and/or - one is required, not both. The "libflashsupport" library causes instability, so don't install it.

```
$ sudo apt-get install libasound2-plugins
```

Then install the Flash 10 beta 1 deb.

i installed the libasound2-plugins package but i am still getting the same error message about both packages (libflashsupport and libasound2-plugins).. even though one of them is already installed..?

---

### Post by olskar on 2008-07-22
Hm, what I did to solve this was to purge libflashsupport and flashplugin-nonfree and then installing flashplugin-nonfree, libasound2-plugins and libasound2 from Intrepid ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)).

Then running: asoundconf set-pulseaudio 

in a terminal.


EDIT: Disregard this post as this was how I fixed it in Hardy.

---

### Post by Sealbhach on 2008-07-22
> **odinfromvalhalla said:**
> Follow my tutorial or just run this [script]("http://www.myscienceisbetter.info/projects/install_flash_player_10_ubuntu64bit") to [install flash player 10 on Ubuntu Hardy 64bit]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

The URL for wget has changed to 0702 - it stopped the script running.

Thanks for the help though, it worked a treat!

.

---

### Post by foxmulder881 on 2008-09-26
What's the story here? I have installed Flash Player 10. Synaptic reports as version 10 being installed, but Firefox only reports version 9.0 being in use.

See screenshot.

**EDIT:** I just done some Googling and have realized there is currently no 64bit version of Flash 10. I can only assume that Synaptic had tried to install the 32bit version on my system, but Firefox was still using the compatible 64bit version 9.0.
Anyway, I've reverted back to version 9.0 in Synaptic too and it now all seems to be fine. 

[IMG]http://img.techpowerup.org/080926/screenshot906.jpg[/IMG]

---

