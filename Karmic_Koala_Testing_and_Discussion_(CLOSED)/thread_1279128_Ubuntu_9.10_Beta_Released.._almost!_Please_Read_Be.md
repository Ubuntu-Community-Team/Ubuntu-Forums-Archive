---
title: "Ubuntu 9.10 Beta Released.. almost! Please Read Before Testing!"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-09-30
The release of Ubuntu 9.10 Beta, the last milestone release before the Release Candidate for Ubuntu 9.10, is imminent. Since we expect many new testers to pick up testing with this milestone, this is a good time to remember some basics regarding testing:

[list][*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their predecided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the beta**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. 


[*] Please wait for the official release announcement that will be posted to the [ubuntu-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce"), regardless of whether the technical overview page seems to be up, and the images seem to be downloadable at URLs posted around forums, blogs or IRC. They may be incomplete, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html") (the link is for the October archives and will be valid once the announcement mail has been sent).


[*] If you're just starting to test Karmic, please take a look at [this wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") for information on various testing methods and good practices.


[*] Once you've started testing, do not upgrade your installation blindly - **especially, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade**. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, always check the list of packages to be removed, upgraded and installed before each upgrade. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed.


[*] When you install the beta, and just keep upgrading your packages until the final release, you'll have the final release; you don't have to reinstall it. But you may want to, in the case that you may be affected by potential unforeseen corner cases that may require a fresh install to fix.


[*] If you run into problems, you're most likely not alone; please do a bug search at [the bug tracker]("https://bugs.launchpad.net/ubuntu") and/or a forum search in this forum (note the "Search this Forum" item on the upper right corner in the thread index) before starting new threads.


[*] [To report a bug]("https://help.ubuntu.com/community/ReportingBugs") in the default desktop applications, use the "Help > Report a Problem" menu item. Where this is not applicable, use the "ubuntu-bug" command line bug reporting tool. You can invoke it by pressing Alt+F2 to open the "Run Application" window, or starting a terminal emulator, and typing ```
ubuntu-bug package_name
``` and pressing "Enter", where *package_name* is the name of the package you want to report a bug in.

If you have trouble finding the right package to report the bug in, take a look at the [Bugs/FindRightPackage]("https://wiki.ubuntu.com/Bugs/FindRightPackage") page on the wiki. If that doesn't help, feel free to start a thread to ask for assistance.

[/list]

---

### Post by blakamin on 2009-09-30
Could you please put "**[SIZE="2"]avoid partial upgrades[/SIZE]**" in bold to save a few dozen questions later (hopefully) [SIZE="1"]and then delete this post.[/SIZE]
Cheers

---

### Post by coldReactive on 2009-09-30
A little early aren't we? Beta, according to the schedule on wiki.ubuntu.com, comes out tomorrow (October 1st) for all of the USA. Not to mention the beta release page on ubuntu.com is not available yet: [http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta)

---

### Post by NoFearDJB on 2009-09-30
> **coldReactive said:**
> A little early aren't we? Beta, according to the schedule on wiki.ubuntu.com, comes out tomorrow (October 1st) for all of the USA. Not to mention the beta release page on ubuntu.com is not available yet: [http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta)

Its reflected in this thread's title: "Ubuntu 9.10 Beta Released.. **almost**! Please Read Before Testing!"

---

### Post by coldReactive on 2009-09-30
> **NoFearDJB said:**
> Its reflected in this thread's title: "Ubuntu 9.10 Beta Released.. **almost**! Please Read Before Testing!"

I didn't see that before I posted it, so yeah, I have selective reading I guess.

---

### Post by andymorton on 2009-10-01
Does anyone know (approximately) what time the beta will be making an appearance? I'm refusing to leave the house until I've updated to it. 

cheers
andy

---

### Post by tjeremiah on 2009-10-01
> **andymorton said:**
> Does anyone know (approximately) what time the beta will be making an appearance? I'm refusing to leave the house until I've updated to it. 

cheers
andy

your pretty much there if you have been with Alpha.

---

### Post by Ulsak on 2009-10-01
> **andymorton said:**
> Does anyone know (approximately) what time the beta will be making an appearance? I'm refusing to leave the house until I've updated to it. 

cheers
andy

You're a lucky guy, I can't get away staying from the work so I have to leave with or without getting the beta..:(

---

### Post by joey-elijah on 2009-10-01
Waiting 2 weeks for the beta is fine, but when you KNOW it's only a few hours away it feels like ageeeeeeeees.

---

### Post by keplerspeed on 2009-10-01
Nice avatar Joey - hope you have gimp ready to update the image to beta, not long now.

---

### Post by joey-elijah on 2009-10-01
> **keplerspeed said:**
> Nice avatar Joey - hope you have gimp ready to update the image to beta, not long now.

Haha thanks :) and yes! i made a new beta version ((^o^))

---

### Post by kreggz on 2009-10-01
is it ready yet? its oct 1 here in Australia

:lolflag:

---

### Post by studavis on 2009-10-01
Ya, same here, waiting......

---

### Post by amendt on 2009-10-01
I think we will wait a little longer for those Australians because those Google Wave developers made us Canadians wait yesterday. :):lolflag:

---

### Post by RaveJunkie on 2009-10-01
I would love a list of new features, fixes and screen shots asap  :)

---

### Post by dino99 on 2009-10-01
> **coldReactive said:**
> I didn't see that before I posted it, so yeah, I have selective reading I guess.

your nickname is buggy: not so cold :lolflag:

that's kiddy attitude fighting their chocolate cup answering every post.

---

### Post by tjeremiah on 2009-10-01
> **RaveJunkie said:**
> I would love a list of new features, fixes and screen shots asap  :)

search throughout the forum :)

---

### Post by gastly on 2009-10-01
Gee it's almost 8pm here in India and it's still not out ... pffft :P 
/me won't be able to sleep today :lolflag:

---

### Post by Giwex on 2009-10-01
Hi Gastly, India as well here and no sign of beta :lolflag:

---

### Post by MacUntu on 2009-10-01
> **kreggz said:**
> is it ready yet? its oct 1 here in Australia

:lolflag:

If it's the Australia I know I hope it's Oct. 2nd. :P

And: WHERE IS THE BETA? :lolflag:

---

### Post by kshrinivas on 2009-10-01
Hmmmm .. Waited for the whole day! No signs of BETA!! :confused:

---

### Post by Technoviking on 2009-10-01
Many of the Alphas came out late in the day UTC time, close to midnight.

T-V

---

### Post by coldReactive on 2009-10-01
> **Technoviking said:**
> Many of the Alphas came out late in the day UTC time, close to midnight.

T-V

Well, that means it's going to be another 6 hours ;)

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-01
Sleepless nights for some of us then : }

---

### Post by ljrmorgan on 2009-10-01
Anyone else want to skip the beta and go straight to the alphas of the next release??!

Don't get me wrong, things breaking really annoyed me, but I'm so impressed at how much things have improved since Jaunty (which I thought was great anyway!) I want to go straight into the next release! :P

---

### Post by mfayaz on 2009-10-01
still 404 on download page! its now 2nd Oct for me

---

### Post by kreggz on 2009-10-01
I am going to do the Steve Balmer monkey boy dance when the beta finally comes out

---

### Post by neglesaks on 2009-10-01
Also waiting eagerly for beta release here in Denmark...

---

### Post by zeroandone on 2009-10-01
> **ljrmorgan said:**
> Anyone else want to skip the beta and go straight to the alphas of the next release??!

Don't get me wrong, things breaking really annoyed me, but I'm so impressed at how much things have improved since Jaunty (which I thought was great anyway!) I want to go straight into the next release! :P
I might do that, but don't know if I can wait for another two months to get the alpha 1 of Lucid Lynx.

---

### Post by yellerKat on 2009-10-01
Looks like [The Register]("http://www.theregister.co.uk/2009/10/01/ubuntu_karmic_koala_beta/") got an advance copy:

> Once I got the 9.10 beta installed on my trusty Toshiba

---

### Post by 23meg on 2009-10-01
> **yellerKat said:**
> Looks like [The Register]("http://www.theregister.co.uk/2009/10/01/ubuntu_karmic_koala_beta/") got an advance copy:

Everyone who has updated her packages in the last day or two has got an "advance copy".

---

### Post by neglesaks on 2009-10-01
> **yellerKat said:**
> Looks like [The Register]("http://www.theregister.co.uk/2009/10/01/ubuntu_karmic_koala_beta/") got an advance copy:


OK, fess up. Who leaked the Beta?

:)

---

### Post by andymorton on 2009-10-01
> **neglesaks said:**
> OK, fess up. Who leaked the Beta?

:)

And why didn't they leak it to us? :P

---

### Post by neglesaks on 2009-10-01
OK, things are happening.

[http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta)

---

### Post by madsc89 on 2009-10-01
Access denied?

---

### Post by 23meg on 2009-10-01
* cough *

> 
Please wait for the official release announcement that will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"), regardless of whether the images seem to be downloadable at URLs posted around forums, blogs or IRC. They may be incomplete, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-September/date.html").



---

### Post by neglesaks on 2009-10-01
403 is better than 404.

---

### Post by ElSlunko on 2009-10-01
Ah! It's things like this that make it hard to concentrate at work.

---

### Post by kshrinivas on 2009-10-01
:popcorn: Yes, I have an updated (till 29th) Karmic as my main OS, but I would like to flush it out & install it clean from live CD. Hope it comes out soon!

> **andymorton said:**
> And why didn't they leak it to us? :P

---

### Post by guillepb on 2009-10-01
> **23meg said:**
> * cough *


Well, regarding that "here" link on the original post, I somehow doubt we are going to see any changes on the **September** archives today... :confused:

---

### Post by 23meg on 2009-10-01
> **guillepb said:**
> Well, regarding that "here" link on the original post, I somehow doubt we are going to see any changes on the **September** archives today... :confused:

Fixed; thanks.

---

### Post by shid007 on 2009-10-01
> **neglesaks said:**
> 403 is better than 404.

Maybe it's some kind of countdown:D

---

### Post by guillepb on 2009-10-01
Thanks for the quick fix! :KS

---

### Post by kshrinivas on 2009-10-01
Things seem to be moving again! Signs :

1. [http://cdimage.ubuntu.com/releases/karmic/beta/](http://cdimage.ubuntu.com/releases/karmic/beta/) has been created, though it has only source under it!
2. Already mentioned [http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta) is alive though status is "access denied"

Which make me believe that build is in progress!

I hope I get it in next few hours!

---

### Post by Squonk07 on 2009-10-01
> **kreggz said:**
> I am going to do the Steve Balmer monkey boy dance when the beta finally comes out

Developers, developers, developers! I'm still obsessively checking every few minutes.

---

### Post by MacUntu on 2009-10-01
It's in the pipeline - now waiting for the official announcement. :)

---

### Post by manit40 on 2009-10-01
nor released rnd between 10 pm and 12pm well thats in the uk so not long ta go guys.........yeah.

---

### Post by lachild on 2009-10-01
Well it up at ****...  But waiting for the announcement as the original post requested. :popcorn:


Edit: Took out url to respect the request of the author that we should all wait.

---

### Post by fitzydog on 2009-10-01
It's only noon here, but I'm dying in anticipation!!!! \\:D/

---

### Post by manit40 on 2009-10-01
out now guys..................<snip>

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-01
Yup it's out, but I will wait for the release notes

---

### Post by ttados on 2009-10-01
Yeah its out but the d/l speeds are quite slow! Not complaining though :)

---

### Post by neglesaks on 2009-10-01
> **&#1057 said:**
> Yup it's out, but I will wait for the release notes

Aye. I'm ready to torrent and seed once downloaded, just need the OK from the release team.

Oh, and to everyone who can (and will) - please download and seed on torrent to take some load off the http servers.

---

### Post by 23meg on 2009-10-01
It's not out until the release announcement says it's out.

---

### Post by Merk42 on 2009-10-01
> **23meg said:**
> It's not out until the release announcement says it's out.

How about it's *out* just not *available*? :)

Is this thread title going to change, and/or get deleted when the announcement hits?

---

### Post by ttados on 2009-10-01
> **neglesaks said:**
> Aye. I'm ready to torrent and seed once downloaded, just need the OK from the release team.

Oh, and to everyone who can (and will) - please download and seed on torrent to take some load off the http servers.


This is very true. I was getting 132kb/sec when I stopped downloading and it hasnt even officially been release yet so lets seed as much as possible.

---

### Post by 23meg on 2009-10-01
> **Merk42]How about it's *out* just not *available*? :)  [/QUOTE]

Let's put it this way, then: For anyone who doesn't want to risk downloading incomplete broken images, and potentially slow down the syncing of mirrors and thus delay the release, it's not out.

[QUOTE=Merk42 said:**
> Is this thread title going to change, and/or get deleted when the announcement hits?

There will be a separate thread; this one will be closed.

---

### Post by beow on 2009-10-01
> **23meg said:**
> It's not out until the release announcement says it's out.

Do they wait until mirroring is done before they publish the release notes? How do I know that my local mirror is updated?

---

### Post by e-Gee on 2009-10-01
It is here [http://news.softpedia.com/news/Ubuntu-9-10-Beta-Is-Available-for-Download-123131.shtml](http://news.softpedia.com/news/Ubuntu-9-10-Beta-Is-Available-for-Download-123131.shtml)

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-01
So can we dl now ?

---

### Post by 23meg on 2009-10-01
> **beow said:**
> Do they wait until mirroring is done before they publish the release notes? 

Multiple people (who are located in different timezones and may thus work at different hours) take care of [the various tasks involved in doing a beta release]("https://wiki.ubuntu.com/BetaProcess"). There's no sure way to tell which comes first, and the safe thing to do is wait for the official release announcement.

> **beow said:**
> How do I know that my local mirror is updated?

By waiting for the official release announcement.

---

### Post by neglesaks on 2009-10-01
> **&#1057 said:**
> So can we dl now ?

No. No release notice on the parent forum, from what i can see.

---

### Post by fitzydog on 2009-10-01
> So can we dl now ? 

Well, the 'official' page still says access denied, so I wouldn't count on it.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-01
Who writes the release notice ?

---

### Post by 23meg on 2009-10-01
> **e-Gee said:**
> It is here [http://news.softpedia.com/news/Ubuntu-9-10-Beta-Is-Available-for-Download-123131.shtml](http://news.softpedia.com/news/Ubuntu-9-10-Beta-Is-Available-for-Download-123131.shtml)

> **&#1057 said:**
> So can we dl now ?

Of course you can, if you want to encourage Softpedia and its likes to continue "me first" linkbaiting to make a few more advertising dollars over a piece of software that hasn't officially been announced.

---

### Post by linbetwin on 2009-10-01
<snip>

---

### Post by 23meg on 2009-10-01
> **&#1057 said:**
> Who writes the release notice ?

[The Ubuntu Release Team]("https://launchpad.net/~ubuntu-release").

---

### Post by ttados on 2009-10-01
I know we all want to download it since technically its out but just quoting the original post:

> Please wait for the official release announcement that will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"), regardless of whether the images seem to be downloadable at URLs posted around forums, blogs or IRC. They may be incomplete, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-October/date.html") (the link is for the October archives and will be valid once the announcement mail has been sent).

We have waited this long we can wait a little longer :)

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-01
> **linbetwin said:**
> <snip>

Seed please

---

### Post by indifference on 2009-10-01
Where can I find a torrent for the CD x86 version?

---

### Post by andymorton on 2009-10-01
<snip>



:)

---

### Post by Squonk07 on 2009-10-01
Well, this page no longer throws up a 403 error.

<snip>

The traffic is gonna be brutal.

EDIT: Damn. I thought I was first. :(

---

### Post by ViRMiN on 2009-10-01
You getting itchy fingers too? :P

---

### Post by andrewabc on 2009-10-01
> **indifference said:**
> Where can I find a torrent for the CD x86 version?

Wait until official announcement and there will be links provided?

---

### Post by 23meg on 2009-10-01
OK, it seems some people are too impatient to read a few lines.

Please read the original post, and wait for the release announcement. I will also post a new thread once the announcement has been posted.

---

