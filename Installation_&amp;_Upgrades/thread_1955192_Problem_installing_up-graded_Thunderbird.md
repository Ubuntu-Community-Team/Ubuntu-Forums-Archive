---
title: "Problem installing up-graded Thunderbird"
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by hatrack on 2012-04-09
I am presently trying to help another OAP up-grade their installation of Thunderbird, running under "Lucid", but we are completely stymied.

I know that the normal repos are hopelessly behind approving s/w so, to obtain a copy of the current version of Thunderbird (11.0.1), I must go either to Mozilla or SourceForge. I have tried installing from down-loaded *.tar packages in the past and I know that this procedure is a real can of worms which I have never been able to get to work so, instead of wasting time with Mozilla, I wish to go to Sourceforge and thus be able to use Synaptic. I therefore need add an "Apt line" within the "Software Sources" applet but I cannot get this to function.

Summarising the problem ---

System -> Admin -> Software sorces 
P/Wd requested, supplied and accepted
Tab "Third-party software" displays list of approved sources (Sourceforge not listed)
Click "Add" button brings up splash screen with legend -- 

"Enter the complete APT line of the repository that you want to add as source"

Now ... I run Hardy on my computer and I have a line for Sourceforge already in Synaptic but, when I copy this into the Software sources applet on my friend's machine, the "Add source" button is greyed out and inoperative.

Can anyone please tell me how I can get an Apt line for Sourceforge that is useable with Lucid. I am afraid that I just don't understand why I'm having this problem or how to proceed and my Ubuntu books seem singularly unhelpful.

Many thanks and Best regards to all

---

### Post by ajgreeny on 2012-04-09
It is best to ad the ppa for the stable version of thunderbird, then install it as normal with synaptic or apt-get.

See [https://launchpad.net/~mozillateam/+archive/thunderbird-stable]("https://launchpad.net/%7Emozillateam/+archive/thunderbird-stable") for the details.

Use commands ```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
```  and you'll see TBrd 11.0.1 is available, and it will then be updated as new TBrd packages appear.

[COLOR=Red]EDIT:  [/COLOR]I have just noticed that you are still runing Hardy.  That is no longer supported so there will be no more updates.

You should really update to a newer version of ubuntu. Lucid 10.04 is nearest to your current Hardy, and still has a year of support on the desktop.  12.04 will be available later this month, but is changed quite a lot from your Hardy, and runs the unity desktop by default.  Try it out and you may love it. It wil have 5yrs support.

---

### Post by hatrack on 2012-04-09
To ajgeeny -- Many thanks for your quick reply to my question ... I knew the answer had to be something simple !

Unfortunately, I can't test this for a day or so because the person whom I am trying to help isn't available but I will do so ASAP and report my findings here, hopefully marking the problem as solved.

As to the fact that I am running under Hardy, I do know that this is "Life-expired" but I am loath to up-grade. I have a dual-boot system (Hardy/WinXP) and when I tried to up-grade to Ubuntu Ver 10 some time ago, the whole process went wrong and turned my system into a right "Dog's breakfast" which took me several days to sort out. In the end, it became a "Format C:" job and involved a complete re-build of the whole system. Now ... I don't particularly like any of the new "features" in Ver 10 or 11 and find that Hardy does all that I want or need (apart from the security aspects). I spent some time recently tightening up the firewall and I'm very cautious as to where I go when on-line. Because I have Sourceforge listed in Synaptic, I can get the latest Vers of T-bird and FireFox and I'm still getting the security up-grades for Hardy, so I don't see any good reason to go through all the rigmarole of up-grading, although I guess I'll have to do this sometime in the future.

With all of that said, I'm always happy to read advice and comments so if anyone wants to put up an alternative argument to that which I have written, I'll most certainly look at this.

Best regards ...

---

### Post by ajgreeny on 2012-04-09
Are you sure you still get security updates for the system?  I thought all packages were still available from the end of life repos, but no further updates were made available for those packages.

---

### Post by hatrack on 2012-04-10
To ajgreeny --

Thank you for commenting again with particular reference to security up-grades.

I must confess that I do not know enough about Linux in general to know whether or not I am receiving security up-grades but, I am receiving something. I am still getting the standard notification that up-grades are available for download and installation and I am simply doing this, as I have always done. The intervals between such notifications is increasing (as one would expect) but still, they come about every 14 days or so and the last has been received since the beginning of April. I view this as a very pleasant bonus (given that Hardy is 'life-expired'). 

From my viewpoint, the later versions of Ubuntu do not seem to offer any real benefits. I have gone to the trouble of actually buying DVDs of each new version and I have run these in demo mode so as to try to make an honest appraisal but I just don't like what I see. I know that I can tweak the settings to get the desktop enivronment I want, so that is not an actual problem (although it does seem rather a waste of effort to have to convert the "new and improved" version back to what I had before the up-grade !). If the newer version had some really important security features then this would indeed be a valid argument for up-grading but beyond a very vague statement that the newer version IS better, I have never seen any objective evidence that this is really so.

I guess that there must be those for whom some new feature is important but for all my uses (email, web access, running spreadsheats and writing letters) Hardy is satisfactory.

Best regards ...

---

