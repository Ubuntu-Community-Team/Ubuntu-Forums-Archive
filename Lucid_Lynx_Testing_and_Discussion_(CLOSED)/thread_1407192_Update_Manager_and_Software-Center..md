---
title: "Update Manager and Software-Center."
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2010-02-15
Im not sure if Software-Center is on track for where it should be with Lucid but i know incorporating Update Manager with SC was a target for the release with Lucid. 

Just curious as to how many people think it should remain separate.

Personally i think it should remain separate.

---

### Post by alexmurray on 2010-02-15
Isn't it a bit too early to say given that no implementation has yet arrived of how this would work?

---

### Post by Merk42 on 2010-02-15
I don't think that was a target for Lucid at all

From the [Wiki](https://wiki.ubuntu.com/SoftwareCenter), emphasis mine
> The Ubuntu Software Center is a graphical utility for package management in Ubuntu. In version 1, it builds on the basic philosophy of Add/Remove Applications with an easier-to-use design. In version 2, the primary feature goals are displaying non-application packages, making PPAs and other repositories more prominent, and allowing ratings and reviews of software. In version 3, we plan to offer commercial software for sale. **Later versions may** include recommendation features, replace other tools such as apturl, gdebi, APTonCD, and most of the Computer Janitor, and **integrate with Update Manager**. 

---

### Post by ronacc on 2010-02-15
I voted don't care on this one since I don't use either .

---

### Post by donniezazen on 2010-02-15
Update Manager, Software Center and Synaptic Manager all are redundant their should be just one application with basic, intermediate and advanced settings.

---

### Post by shafin on 2010-02-15
Thats the plan with software center. It has already replaced gnome-add-remove and will gradually replace synaptic and update manager.

---

### Post by dino99 on 2010-02-15
vote too for a fatless ubuntu distro ](*,)

---

### Post by emarkay on 2010-02-15
Seems stupid to me - one is to update/fix *existing* packages, while the other is to* add* new ones.

---

### Post by gjoellee on 2010-02-15
Put everything into Ubuntu Software center...it will be the "modern" Synaptic!

What's the point of having Synaptic, Update Manager and Ubuntu Software Center, if all the functions of the different software can be ported into one single program? That is way easier. The menus will be shorter, and there are less software to care for, both for users and maintainers!

---

### Post by Simian Man on 2010-02-15
Or they can just adopt Packagekit which already does what they seem to want and does it well.

---

### Post by 23meg on 2010-02-15
> **Simian Man said:**
> Or they can just adopt Packagekit which already does what they seem to want and does it well.

PackageKit is a backend, and is thus extraneous to this discussion. If you mean gnome-packagekit, it doesn't quite (and isn't meant to) deliver the experience desired of future versions of Software Center. This was discussed extensively last cycle; a search in the Karmic forum would reveal the various arguments.

---

### Post by KrazyPenguin on 2010-02-15
My reason is Ubuntu-Tweak, has both built into one device.
I would like to see Ubuntu-Tweak or something "very similar to it", default in Ubuntu.

---

### Post by Slug71 on 2010-02-16
> **Simian Man said:**
> Or they can just adopt Packagekit which already does what they seem to want and does it well.

Packagekit will mostly likely replace apt-daemon as the backend to USC in Lucid +1. 
In which case PK's Update System would replace Update Manager if they were to remain separate.

But yeh, updating should be separate to installing/managing software.

---

### Post by seeker5528 on 2010-02-17
> **Slug71 said:**
> Packagekit will mostly likely replace apt-daemon as the backend to USC in Lucid +1.

Do you have a link to something indicating that might be the case?

Package Kit may provide enough to allow an update manger to be created that handles the security up dates without any big issues.

Package Kit isn't designed to provide the level of control to do all the things Synaptic does. Probably tons of room for debate, but personally I don't think Package Kit provides enough for Software Center either even for the small number of features desired to consider it a replacement for Synaptic.

I'm also highly skeptical that anything using Package Kit could handle distribution upgrades anywhere near as well as update manager.

Later, Seeker

---

### Post by Slug71 on 2010-02-17
> **seeker5528 said:**
> Do you have a link to something indicating that might be the case?

Package Kit may provide enough to allow an update manger to be created that handles the security up dates without any big issues.

Package Kit isn't designed to provide the level of control to do all the things Synaptic does. Probably tons of room for debate, but personally I don't think Package Kit provides enough for Software Center either even for the small number of features desired to consider it a replacement for Synaptic.

I'm also highly skeptical that anything using Package Kit could handle distribution upgrades anywhere near as well as update manager.

Later, Seeker

No links but things having been going well in the Packagekit mailing list regarding the relationship with PK and debconf which was the big reason USC was chosen over PK and aptdaemon written instead of using PK as the backend to USC in the first place. However aptdaemon borrows a lot of code from PK.

They pretty much have a plan now how to make the the two work, and i believe PK is all set for it and debconf and the PK backend just need some code. Also i think Colin Watsons approval is just needed on the idea.

This whole subject going on in the mailing list was started for including PK in Ubuntu though.

This was the blueprint for Lucid but they hadnt yet got as far in the discussion as they have now to the point where they have a game plan.

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-backend](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-backend)

---

### Post by seeker5528 on 2010-02-18
> **Slug71 said:**
> This was the blueprint for Lucid but they hadnt yet got as far in the discussion as they have now to the point where they have a game plan.

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-backend](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-backend)

From that it sounds like things are looking up a little bit for Package Kit.

Other than the debconf thing the other big weak point that I've always seemed to run into with the package managers that use Package Kit was conflict resolution, if there are conflicts or other oddities with dependencies or anything weird happens while installing packages they seem much more prone to do the wrong thing or not recover than package managers that use a more direct line of control.

If the conflict resolution is done first and Package Kit is only used for the actual installation/removal I could see the working out. Still some question about how robust it is relative to issues that arise during the installation.

Getting back to the topic of this thread.

I still think we need Update Manager for the distribution upgrades and that it should remain separate. 

It doesn't seem like it should be that big of a deal to build the function in to Software Center to check for new versions of the distribution, then hand things off to Update Manager if the user chooses to upgrade and I do think it would be good to have Software Center handle the security updates. 

In the end I don't think user opinion should really factor in that much, the primary question is 'What's easier to maintain?'..... 

[list]A: Software Center with all the Update Manger functions rolled in.[/list]

[list]B: Add the functions to Software Center to handle the security updates and remove the functions from Update Manager that are not necessary if it will only be used for distribution upgrades.[/list]

[list]C: Keep things as they are using Software Center for adding/removing software and using Update Manger for all security updates and distribution upgrades.[/list]

Later, Seeker

---

### Post by xebian on 2010-02-18
> **seeker5528 said:**
> ...

...
I still think we need Update Manager for the distribution upgrades and that it should remain separate. 

It doesn't seem like it should be that big of a deal to build the function in to Software Center to check for new versions of the distribution, then hand things off to Update Manager if the user chooses to upgrade and I do think it would be good to have Software Center handle the security updates. 

In the end I don't think user opinion should really factor in that much, the primary question is 'What's easier to maintain?'..... 

[list]A: Software Center with all the Update Manger functions rolled in.[/list]

[list]B: Add the functions to Software Center to handle the security updates and remove the functions from Update Manager that are not necessary if it will only be used for distribution upgrades.[/list]

[list]C: Keep things as they are using Software Center for adding/removing software and using Update Manger for all security updates and distribution upgrades.[/list]

Later, Seeker

Did you just describe Synaptic?  It's already here.  

Synaptic maintainer = Michael Vogt = lead dev for USC.  No wonder it looks like Synaptic, only uglier. :)

---

### Post by zekopeko on 2010-02-18
> **xebian said:**
> Did you just describe Synaptic?  It's already here.  

Synaptic maintainer = Michael Vogt = lead dev for USC.  No wonder it looks like Synaptic, only uglier. :)

Michael is implementing a spec made by Matthew P. Thomas. And USC IMO looks good if you change the background color to something sane.

---

### Post by seeker5528 on 2010-02-18
> **xebian said:**
> Did you just describe Synaptic?  It's already here.  

Synaptic maintainer = Michael Vogt = lead dev for USC.  No wonder it looks like Synaptic, only uglier. :)

LOL!!!

For me personally, you would have to hit my cold dead HDD with an EMP to get Synaptic off of it, but it's interface is a bit busy and I expect many of it's fuctions are more of a disctraction than a help to the average user, and it has it's own quirks with dependency resolution.

Relative to needing the ability to easily search for and select individual packages to try to work around quirks with dependency resolution, keeping the distribution up to date, and being informed of new packages during a development cycle, I can't really see a day where Software Center could be considered a replacement for Synaptic. 

Relative to what Synaptic provides versus what you need for maintenance and installation in stable release, Software Center doesn't need a big list of features to be considered a replacement for Synaptic.

Even if you stick to the stable releases, use of PPAs or other unofficial package sources may dictate the desire to use Synaptic or some other package manager that is more feature rich than Software Center.

Software Center is designed to provide software management rather than package management so by definition some package management features are outside the scope of what it is intended to provide. 

Later, Seeker

---

### Post by xebian on 2010-02-18
> **seeker5528 said:**
> ..
...
Software Center is designed to provide software management rather than package management so by definition some package management features are outside the scope of what it is intended to provide. 

Later, Seeker

Software in Ubuntu comes in packages.

---

### Post by seeker5528 on 2010-02-19
> **xebian said:**
> Software in Ubuntu comes in packages.

It's a logic thing. 

Just because you have a BFL of packages doesn't mean you have to show the user a BFL of packages.

If the design decision is made that instead of just showing a BFL and having to search for all Firefox related packages, you want the user to be able to go to 'Internet --> Firefox' to get a page with the option to install Firefox and have the option from there to see a list of relevant add ons with the option to select the ones you one and deslect the ones you don't, that dictates to some extent the type of features that will or won't be added. 

For the most part if a feature doesn't fit that 'It's a software manager not a package manager' concept, it's not likely to be added or at least not a high priority. At least that's the way I'm interpreting the situation based on previous discussion.

[http://ubuntuforums.org/showthread.php?t=1341164](http://ubuntuforums.org/showthread.php?t=1341164)

It's easy to make an exception for updates because you are just presenting the user with a list of things they already have installed.

Later, Seeker

---

### Post by katie-xx on 2010-02-19
[SIZE=2][COLOR=Blue]I must admit I find the separation of update and install to be logical.
Im always willing to be proved wrong or persuaded otherwise though

Kate[/COLOR][/SIZE]

---

### Post by Tibuda on 2010-02-19
> **emarkay said:**
> Seems stupid to me - one is to update/fix *existing* packages, while the other is to* add* new ones.

This is what I think too. It makes sense for them to be separated.

---

### Post by cariboo on 2010-02-19
I use Synaptic to fix, update and install packages.

---

### Post by CJN on 2010-02-20
I dunno, to me updating and installing new software are really quite similar in Linux. I only ever install software on a whim in Linux (I use many different OS') because everything is so ramshackle anyway that I don't care if something might seem out of place because nothing possibly could, also there is a much lower risk of *supported/In-PPA* software being malicious.

So whether a new version of a program just came around, or I just installed a new app to give it a whirl the experience is very similar both in practice and in experience.

Though it's an interesting discussion so please tell me something I'm missing because I'd love for this thread to keep going.

---

