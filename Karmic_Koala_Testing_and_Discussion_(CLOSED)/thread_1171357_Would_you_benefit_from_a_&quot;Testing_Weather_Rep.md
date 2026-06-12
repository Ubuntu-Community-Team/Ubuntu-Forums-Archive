---
title: "Would you benefit from a &quot;Testing Weather Report&quot;? What should it include?"
date: 2009-05-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-05-27
During the Karmic cycle I'm planning to develop a "Testing Weather Report" web application (inspired by [its counterpart developed for the release team]("https://blueprints.launchpad.net/ubuntu/+spec/developer-weather-report")), which will display various bits of information on the state of the development branch. 

The information I plan it will aggregate would involve, but is not limited to:

[list][*] Held back packages
[*] Critical bugs in core packages (kernel, gcc, glibc, etc.) that may have high impact on a broad range of testers
[*] Ongoing library transitions
[*] Archive integrity
[*] Daily image build status
[*] Daily image health check (oversized or not)
[*] ISO package diff (how up-to-date are the current ISO images with the archive?)
[*] Upgrade situation ( possibly with automatic upgrade test results)
[*] Current milestone, release notes / technical overview, next milestone name, how many days are left
[*] Freeze status (freezes we are on and upcoming ones)
[*] New packages in the archive
[*] Bugs targeted for the next milestone
[*] Calls for testing of specific packages (possibly not yet pushed to the development branch) by developers
[*] Significant updates in components related to release goals
[*] Archive mirror status
[*] Build daemon status
[/list]

It's worth emphasizing that all of this information is already available to testers, but is scattered over various resources, and can be hard to evaluate altogether at a single time point. The goals are to:

[list][*] come up with a list of most relevant metrics and other data that will help testers
[*] display the data in a manner in which the most relevant elements can be evaluated at a single glance, on a single page, and the slightly less relevant can still be easy to reach
[*] present it all on an attractive web page that will hopefully present a small bit of extra incentive for people to do testing for Ubuntu.
[/list]

The feedback I'm hoping to get would be on: 

[list][*] whether you'd find this useful at all and why
[*] what kind of information you'd want aggregated by it, in addition to what I've listed above
[*] what particularly useful ways of displaying the information would be (don't worry, I do have some ideas).[/list]

I'll be holding a session tomorrow on the QA track at [UDS-Karmic]("https://wiki.ubuntu.com/UDSKarmic") to lay down the initial plan and get preliminary feedback. Those interested can [tune in]("http://icecast.ubuntu.com") to room #9 at 14:15 UTC tomorrow to follow up, and participate live via IRC (#ubuntu-devel-summit on Freenode) and Gobby (gobby.ubuntu.com - document name will be "karmic-qa-testing-weather-report"). I'll also keep you posted once I have some mockups and rudimentary code.

---

### Post by Bou on 2009-05-27
I definitely would!

---

### Post by davideotape on 2009-05-27
> **Bou said:**
> I definitely would!

+1 :guitar:

---

### Post by xebian on 2009-05-27
I thought it was some kind of a new weather forecast app that need testing. :p

---

### Post by cjsteele on 2009-05-27
I would think that having substantial discussions before-hand about how you propose to model this would be useful.  

Might I suggest that each of the metrics you're mentioning be modeled on their own (for trending- up/down) and that an aggregate model also be developed? 

I'm just a stats n00b, but know enough about logarithmic normalization and similar trending techniques that I *might* be able to contribute to something.  

Best
-C

---

### Post by jerrylamos on 2009-05-27
Good idea!

Some of the time we spend re-discovering the wheel, chasing bugs that are already defined.  Yes, I try to find out what's known to be broken but I find the info scattered.

I'd rather spend time on what's new/changed/fixed to get some early feedback to whoever may be interested.

Jerry

---

### Post by 23meg on 2009-05-27
> **cjsteele said:**
> I would think that having substantial discussions before-hand about how you propose to model this would be useful.  

Might I suggest that each of the metrics you're mentioning be modeled on their own (for trending- up/down) and that an aggregate model also be developed? 

I'm just a stats n00b, but know enough about logarithmic normalization and similar trending techniques that I *might* be able to contribute to something.  

Best
-C

I feel you're misinterpreting the goal. I'm not really planning this to do any statistical computation with the data, at least at this point; it will merely pull all the data together as they are at a given time point (of viewing the page) and display it all in a convenient and well-designed "dashboard".

---

### Post by ranch hand on 2009-05-27
Yes, I believe that would be a great tool.

One thing that it would do is to help those of us that are new at this to see were we should be looking and some idea what we should be doing.

---

### Post by davideotape on 2009-05-27
I don't know how hard it would be to set this up, but someone could create an automated twitter feed that tweets updates whenever the information you're aggregating changes.

---

### Post by ghindo on 2009-05-27
Yes, please.  I think we would all benefit greatly from having all that testing information gathered in one place.

---

### Post by ronacc on 2009-05-27
sounds good to me 23meg , go for it !

---

### Post by tawmas on 2009-05-27
Great! I think I'd use it daily if it existed. Even more often when there are serious bugs open...

---

### Post by fifth on 2009-05-27
Would definitely use such a resource. I think it would be very useful.

---

### Post by Didius Falco on 2009-05-27
I would definitely use it.

On Edit: Thank you for taking your time to work on it.

---

### Post by ktp on 2009-05-27
> **xebian said:**
> I thought it was some kind of a new weather forecast app that need testing. :p

:lolflag:

---

### Post by autocrosser on 2009-05-27
I'm all for it--thank you for thinking of it!!!!!

---

### Post by Darkshade on 2009-05-27
> **xebian said:**
> I thought it was some kind of a new weather forecast app that need testing. :p
Me too :lolflag:

On topic - I think it would be really useful. Thank you :)

---

### Post by ronacc on 2009-05-28
a request , the "calls for testing" should contain links to the software they want tested if they haven't reached the normal repos yet .

---

