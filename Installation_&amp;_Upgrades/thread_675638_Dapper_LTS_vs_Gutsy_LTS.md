---
title: "Dapper LTS vs Gutsy LTS"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by FishFoot on 2008-01-22
Hey Guys,

I've got a tough question and its tougher to phrase the heading of the post well, but here goes. 

I've been working for the past 9 months on a completely rebuilt Windows / Ubuntu Linux based corporate network infrastructure.  At the beginning of the project the only LTS version that was available was Dapper and it suited all of our needs quite well.  There was robust documentation and an ample supply of howtos over at HowtoForge.  

Along the way we've used "evaluation" hardware to create a mock up of the network and get everything running nicely.  We've had the chance to test different pieces of software and the ways in which they interact and so far we haven't had any major issues.  The last piece of the project is to incorporate a pair of 1 TB Raid 1 arrays that are connected to our Dirvish backup server via an eSATA cable.  Unfortunately though Dapper appears to have very limited support for hotswapping the SATA arrays.  It appears that my only option with dapper (kernel 2.6.15) is to power down the machine to swap the arrays.  As this has to be done daily and by a non-tech this is a less than desirable solution.

I went ahead and tested out Gutsy today on the same machine to find that hotswapping the eSATA devices works perfectly.  This was really mixed news.  I am now faced with a difficult decision:

1) Upgrade the dirvish machine to Gutsy and the 4 other ubuntu boxes stay Dapper.
2) Build a custom kernel with the support that I need for SATA hotswapping built in
3) Upgrade all the machines to Gutsy.
4) Use USB2 which functions at about 1/3 the speed.

None of these options look particularly appealing to me but I have to say that an across the board upgrade to Gutsy seems like the best bet.  Here's the problem though.   I assume that my config files will still work for the various pieces of software I'm using, but I really don't have time to test the environment.  As I said these machines (as dapper machines) have had months of sitting there doing their jobs in a test network.  Here at the last minute I'm going to switch to the newer OS but I can't QA the same way.

My question is this:
Do I face any serious repercussions  by upgrading all the machines to Gutsy?  Here are the pieces of software I am using (predominantly):
* Postfix
* Mailscanner
* Spamassassin
* clamAV
* dirvish
* samba
* winbind
* ssh
* virtualbox

Any help or guidance would be much appreciated.

Thanks
FishFoot

---

### Post by bazzer on 2008-01-23
Well, I can't specifically help you with the applications you've listed but I share your sentiment! I began customising a Dapper LTS CD to use in a corporate environment. I chose the LTS as it was marketed as being the best option for corporate use at the time.

And I slogged and slogged over it! Only to come up against a problem I couldn't solve relating to SANE not recognising my scanner. So I just tried Edgy (was a while back!) and customising that. Which was a lot less hassle than I thought.

So now, I try to keep abreast of the release schedule, and customise the latest it.

Also, maybe worth remembering too, Hardy Heron will be LTS too.

---

### Post by FishFoot on 2008-01-23
Yeah, I saw that.  I had made a mistake thinking that Gutsy was LTS.  In some ways this made the choice easy for me.

We're going to custom build the kernel and run with that for a couple of months.  I think when the Hardy is released in April we'll look to make the upgrade.  No way I'm going to do that through the apt-get upgrade process though.  We'll just go with new hard disks and fresh installs.  I think that will be a lot simpler.

I'm hesitant to upgrade servers unless absolutely necessary.  I think it would be of great help to the Ubuntu community users who use the system in a corporate environment if there was a clear statement as to the differences between the various LTS systems when they are released.  It would be nice to know what software will continue to work and what won't.

Anyway, thanks for the reply.
FishFoot

---

### Post by DrMega on 2008-01-23
The next version (can't remember its name but it is going to be 8.04) is going to be an LTS. Why not wait for that?

---

