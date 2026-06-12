---
title: "Natty: Update Manager Can Not Remember Last Update"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-05-07
Hello,

***Update Manager*** does not remember latest update.[IMG]http://3.bp.blogspot.com/-uCR4G2-v82M/TaB4mRy3ugI/AAAAAAAACGE/JGoOR8fja5A/s400/forgot.jpg[/IMG]

Since I upgraded to Natty ***Update Manager*** does not remember the last time that the system  was updated.

I upgraded to Natty about a week ago; and I have been updating the system packages everyday; but Update Manager gives the following message:

***The package information was last updated 7 days ago.***

Apparently the code that is supposed to keep track of the update history is not running, or the log file is either; ***not-present, corrupt, or has improper-permissions.***

---

### Post by coljohnhannibalsmith on 2011-05-07
Oh no,

Now I'm getting the ***red triangle with exclamation mark*** in the indicator-applet; that tells me that the ***"Update Information is Out of Date",*** when I mouse-over it.

Then, when I click on it, Synaptic launches, 'not' Update Manager. 

Jeeze, what next...

[IMG]http://www.fda.gov/ucm/groups/fdagov-public/documents/image/ucm231533.jpg[/IMG]

---

### Post by coljohnhannibalsmith on 2011-05-11
I've thought about using **Synaptic Package Manager** to completely remove & replace the following packages; ***update-manager, update-manager-core, & update-notifier.***  This would force a fresh copy of these pacakges *and* their configuration files to be written to disk, hopefully eliminating any corrupt files.  However, when I marked 'any' of these for removal, they all wanted to remove ***ubuntu-desktop,*** which appears to be a disasterous situation.

Can anyone tell me if removing then reinstaling ubuntu-desktop will hose my OS or desktop configurations?

BTW, I haven't been able to locate any log-files associated with update-manager, or I would try to replace *these* before attempting any of the drastic actions mentioned above.

[IMG]http://www.thinkpads.com/wp-content/uploads/2009/07/latitude_e6400_firehose.jpg[/IMG]

---

### Post by coljohnhannibalsmith on 2011-05-13
Hello,

After reading some of the Natty configuration docs; I decided it was reasonably safe to ***try***  what I had been considering in the OP; so from [COLOR=Red](Ubuntu-Classic)[/COLOR] I...

Used **Synaptic Package Manager** to completely remove & replace the following packages; [B][I]update-manager, update-manager-core, update-notifier, update-notifier-common.


[/I][/B]This action also forced the removal of the following packages:

***ubuntu-desktop (Unity?), computer-janitor, & computer-janitor-gtk***

When I reinstalled ***all*** of these packages the problem was 'not' resolved.


Can anyone offer an opinion as to what might be going-on here:confused:




Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-15
Well,

I was just thinking that since I have Ubuntu Tweak installed, and it's able to lauch update-manager from within its GUI, there just might be some kind of conflict between the two of them.  So, I completely removed Ubuntu Tweak, so that the configuration file(s) would also be removed; and then tried update manager again twice, so that I could see if it would then remeber the latest update; but it did not.

I then booted into the 35-9 kernel, to see if ***'this'*** made a difference; but it did not.

What I'm thinking now, is that it must be the log or history file that this package uses that's corrupt or is somehow 'not' being updated.  I don't think 'log' files would be removed during a complete-package-removal.  Can someone verify this???

Also, does anyone know what the name of this log file is; so that I can try to recreate it, or change its permissions???

[IMG]http://4.bp.blogspot.com/_iYgJ1nxfX9w/SYG3sjqq2tI/AAAAAAAAAOU/aNnDGsgi1H8/s320/screenshot1.png[/IMG]




Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-17
This problem now appears to be solved...

To view the solution please see the following thread:

[http://ubuntuforums.org/showthread.php?t=1745608&page=2](http://ubuntuforums.org/showthread.php?t=1745608&page=2)

[IMG]http://tshirtgroove.com/wp-content/uploads/2008/10/problem-solved-tshirt.jpg[/IMG]

---

