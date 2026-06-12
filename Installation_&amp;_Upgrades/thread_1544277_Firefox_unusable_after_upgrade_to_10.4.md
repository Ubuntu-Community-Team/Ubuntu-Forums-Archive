---
title: "Firefox unusable after upgrade to 10.4"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by bob12564 on 2010-08-02
I upgraded to 10.4 2 weeks ago and so far Firefox is a mess.  I've read about people having crashes but that's not my problem.  It opens fine and seems to run OK but strange things are happening.  For example:

1) When closing Yahoo email there is supposed to be a redirect to Yahoo.com.  The page opens but it's all text and not rendered properly at all.

2) Strange certificate errors occur. For example, I try to go to ebay.com and I get a cert problem.  Examining "details" I discover that Firefox is trying to match the cert for Yahoo for the current page which is ebay.

3) I use the Google quick search function for "efax forums".  Google opens and I get link to SourceForge.  I click it and I go the the main Google search page instead of SourceForge.

I could go on.  

10.4 has been out for over 3 months and I can't believe it's this buggy.  I have no interest in doing a full install and spending hours reinstalling programs and data.  Upgrade has always worked in the past.

Does anyone know what's happening?

Thanks.

---

### Post by ahbart on 2010-08-02
> **bob12564 said:**
> 10.4 has been out for over 3 months and I can't believe it's this buggy.  I have no interest in doing a full install and spending hours reinstalling programs and data.  Upgrade has always worked in the past.
Does anyone know what's happening?
Thanks.
You have problems with firefox and blame Ubuntu Lucid? :shock:

You could try renaming the .mozilla folder tot .mozilla-backup
and start firefox and see if the problems have been 'fixed'.

---

### Post by lovinglinux on 2010-08-02
Most likely creating a new profile will fix it. Nevertheless, you could try to simply move the file **secmod.db** from your Firefox profile to another, since it is known to be causing problems. You need to do that with Firefox closed.

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial and [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by bob12564 on 2010-08-03
The new profile did not fix the problem.  Today, for example, I cannot access Yahoo's home page normally.  It just shows up as text.

The reason I am suspecting the 10.4 upgrade is because I've read that others are having problems with Firefox after upgrading.  There was a problem accessing pages with Flash and that seems to be fixed now.  I also read something about an architectural change in Ubuntu that caused some problems with Firefox being able to access pages with Java code.  Another program I use, efax-gtk, also stopped working because of an architectural change but I read about a fix for it that requires a newer version than the one shipped with 10.4.  But back to Firefox...

I'll try the tweeks suggested and I'll keep reading.

Thanks for the help.

---

### Post by lovinglinux on 2010-08-03
Try to create a new Ubuntu user, just for testing. Log in with the new account and check if the problem persist. If not, then most likely you have some old gnome settings causing trouble.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

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

### Post by bob12564 on 2010-08-04
Hello,

Thanks for the help.

I have the diagnostic info you requested.  Thank you for making the instructions so simple.

The problem with Yahoo is intermittent.  I know that Yahoo intermittently posts a Flash video on the home page which suggests a Flash issue, but I've been able to access You Tube without any problems and the videos play normally.  After I had the latest Yahoo problem I went to Google to read more about the problem and received a certificate warning when I tried to select one of the links.  The link was to dslreports.com.  Here's what Firefox reported:

[www.dslreports.com](www.dslreports.com) uses an invalid security certificate.

The certificate is only valid for addons.mozilla.org

(Error code: ssl_error_bad_cert_domain)


I'm not sure what that means but "addons" seems curious.

Here is the Shockwave ionformation and Firefox/About window which doesn't say much:

Finally, the rest of the information you requested:


Ubuntu Architecture

Linux asus-p4p800 2.6.32-24-generic-pae #38-Ubuntu SMP Mon Jul 5 10:54:21 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-3.5					install
firefox-3.5-branding				install
firefox-3.5-gnome-support			install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-08-04
> **bob12564 said:**
> 
The problem with Yahoo is intermittent.  I know that Yahoo intermittently posts a Flash video on the home page which suggests a Flash issue, but I've been able to access You Tube without any problems and the videos play normally. 


Some users can play YouTube videos normally, but can't when the video is embedded. That could be the source of your problem. In this case, allowing third-party cookies could help.

> **bob12564 said:**
> After I had the latest Yahoo problem I went to Google to read more about the problem and received a certificate warning when I tried to select one of the links.  The link was to dslreports.com.  Here's what Firefox reported:

[www.dslreports.com](www.dslreports.com) uses an invalid security certificate.

The certificate is only valid for addons.mozilla.org

(Error code: ssl_error_bad_cert_domain)

I'm not sure what that means but "addons" seems curious.


The addons.mozilla.org is the Mozilla site where Firefox extensions are published. It is a safe site. Nevertheless, I don't see a reason why another site would display a certificate error. Which makes me believe could be a problem with secmod.db and cert8.db. Several users are experiencing certificate issues.

Another possibility is that the link you selected was redirected to an extension hosted on Mozilla.

There is also one thing that I suspect. Google provides prefetching, which means Firefox will download the content of some sites in the Google results that you probably would visit, in order to speed up page loading. One of these results could be linked to Mozilla. That happened to me some time ago.

To disable prefetching, type **about[noparse]:[/noparse]config** in the address bar, then type **network.prefetch-next** in the filter and then double-click int he result to make it **false**.

> **bob12564 said:**
> Here is the Shockwave ionformation and Firefox/About window which doesn't say much:

Finally, the rest of the information you requested:


I can't identify anything wrong with your Firefox setup. Nevertheless, since you had upgraded, would recommend purging it and install again.

```
sudo apt-get purge firefox 
sudo apt-get purge firefox-3.5
sudo apt-get update
sudo apt-get install firefox
```

I know you don't want to do a clean install, but I would recommend creating a separate partition for home and always doing clean installations when a new Ubuntu release is available. It doesn't take time and you can get your system back exactly the way it was in no time. Take a look at my extension [Umarks]("http://umarks-extension.blogspot.com"). It allows to restore all your programs and repository sources.

I just did a clean install other day, because I wanted to test the 32bit version of Ubuntu. What I do is to install it preserving the home partition, then I start Firefox run Umarks to install all my programs and voilà...everything works as before. The only boring thing I need to do is to restore a couple of config files for my TV card and remote, that are saved in the /etc folder and thus are wiped by the clean install.

I never did an upgrade since I started using Ubuntu. Only clean installs.

---

### Post by bob12564 on 2010-08-10
I did the uninstall/reinstall of Firefox as suggested and the problems persist.  The uninstall removed the Gecko-Gnome media player and I manually reinstalled it from Synaptic.

Some new symptoms, many of which are intermittent:

1) I exit Yahoo mail and instead of auto-directing to the Yahoo home page I end up on the home page for WOT, one of the Firefox add-ons.  

2) I search in Google and several of the search links error as non-existent URLs.

3) I go to the Yahoo home page and it opens normally.  A Flash video in the news section plays but a Flash video on a sidebar says the page doesn't exist.

4) This one is consistent: I cannot watch any Flash video full screen.

I've seen other complaints about 10.4 and Flash problems in Firefox but I expect that would have been fixed by now.

Other than the Flash problems, the link error and certificate might suggest that Firefox is losing track of where it is and where it's trying to go.

I'm stumped.

---

### Post by lovinglinux on 2010-08-10
Create a new Ubuntu user and login with that account just to test if the problems persist. If not, then it is some gnome settings fault, since a clean Firefox profile has already been created and didn't help.

---

### Post by bob12564 on 2010-08-19
I tried creating a new user but I found it confusing.  For example, I didn't get the usual shut down icon on the upper right.  I couldn't figure out how to turn off the computer.  I deleted the test user and went back to the main user.

I deleted Firefox and reinstalled but no change.  I then deleted my Firefox add-ons.  Then things seem to stabilize, maybe because of the removal of the add-ons or because of system updates from Ubuntu.  But there's another problem I detected with Firefox: I'm trying to re-add the add-ons and I'm getting "-228 Download Error" messages for 2 days now.  The Firefox add-on service seems to be working on my other computer which is on Ubuntu 9.10.  Mozilla suggests some reasons for the error such as network or firewall problems or a legitimate problem on their end.  

I may have found a temporary solution to the Flash full screen problem.  I had no problems with full screen Flash in You-Tube but everywhere else all I get is a white screen.  Other people have the problem and the workaround is to shut off hardware acceleration.  Never had to do that before.

I could be convinced into doing a fresh install is I could be convinced that everything would work normally.

Thanks for the continued help.

---

### Post by salima on 2010-08-19
just cruising for now and noticed this thread...

i am having the same problems and was having them while i was still on windows. i also thought it was a firefox problem or a windows problem but it has carried over with me to 8.10, though it is way better than it used to be. it all started when the frethoog got into my machine...

the two main sites i am having the most trouble with are yahoo and google (which includes google mail and their search engine) i was wondering if there is actually something wrong with them? 

what about downloading another browser and using that for a test? i was considering that, but dont know which would be best for linux...

---

### Post by lovinglinux on 2010-08-19
> **bob12564 said:**
> But there's another problem I detected with Firefox: I'm trying to re-add the add-ons and I'm getting "-228 Download Error" messages for 2 days now.  The Firefox add-on service seems to be working on my other computer which is on Ubuntu 9.10.  Mozilla suggests some reasons for the error such as network or firewall problems or a legitimate problem on their end.

Instead of clicking the "Install" button, right-click, select "Save link as", save the xpi file in your Desktop, then drag it to Firefox.

> **bob12564 said:**
> I may have found a temporary solution to the Flash full screen problem.  I had no problems with full screen Flash in You-Tube but everywhere else all I get is a white screen.  Other people have the problem and the workaround is to shut off hardware acceleration.  Never had to do that before.

Try the third item on [this list]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").


BTW, Yahoo and Google issues could be because Adblock Plus. I have experienced issues with it this week.

---

### Post by bob12564 on 2010-08-19
I tried the "save link as" and I get "unable to connect...".  AdBlock was one of the add-ons I already removed.

I discovered another site I can't reach.  It's reached via a link on a webpage.  Yesterday Firefox put me on MySpace when I clicked the link (wrong, no relation) and today it's sending me to Adobe.  Makes no sense.  It's like a domain name server is corrupted.  But no problems on the 9.10 machine.

I loaded Epiphany web browser today and I still cannot reach that website.  I get the "unable to connect" message which may be a tad better than going to the wrong site.

Maybe the problem is outside of Firefox.  I checked my ethernet settings because I saw something about IPV6 settings causing some sites to be unreachable but I have that set to "ignore".

It's beginning to look like I need to do a fresh install of 10.4 or use CLonezilla to clone my 9.10 drive from my other machine.

I know many people don't like to do upgrades but I've done 4 of them and they always worked.  This is disapointing.

---

### Post by lovinglinux on 2010-08-19
> **bob12564 said:**
> Maybe the problem is outside of Firefox.  I checked my ethernet settings because I saw something about IPV6 settings causing some sites to be unreachable but I have that set to "ignore".

I don't think that would be enough. Would be better if you disable ipv6 in Grub. See the 5th item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by mörgæs on 2010-08-20
> **salima said:**
> ... but it has carried over with me to 8.10 ...

8.10 is unsupported and hence a security threat. I would recommend that you switch to one of the supported releases.

---

### Post by bob12564 on 2010-08-20
Disabling IPV6 in Firefox worked.  I was able to access the add-on site.

The Flash problem was fixed by disabling hardware acceleration.

Thanks for both suggestions.  Just one last question:  My 9.10 machine uses the same DSL modem/router and IPV6 is enabled in Firefox and it works fine.  Flash is also set to use hardware acceleration.  What changed in 10.4 to cause these problems?  And, for that matter, did I simply cure a symptom rather than the underlying problem?

Thanks again for the help.

---

### Post by lovinglinux on 2010-08-20
> **bob12564 said:**
> Disabling IPV6 in Firefox worked.  I was able to access the add-on site.

The Flash problem was fixed by disabling hardware acceleration.

Thanks for both suggestions.  

You are welcome.

> **bob12564 said:**
> Just one last question:  My 9.10 machine uses the same DSL modem/router and IPV6 is enabled in Firefox and it works fine.  Flash is also set to use hardware acceleration.  What changed in 10.4 to cause these problems?

I don't know.

> **bob12564 said:**
> And, for that matter, did I simply cure a symptom rather than the underlying problem?

The problem with ipv6 is common and this is one of the first things I disable after a clean install. Until ipv6 is widespread and available through most internet providers, I guess we will have to live with it.

---

