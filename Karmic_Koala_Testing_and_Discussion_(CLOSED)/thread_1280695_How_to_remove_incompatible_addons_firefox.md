---
title: "How to remove incompatible addons firefox?"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-10-02
After the upgrade firefox reports some incompatible addons:
firefox (en) 3.0.7
Xulrunner (en) 1.9.1.2
These where probably left behind from the previous firfox.
The problem is that the enable and uninstall buttons are both disabled. So how do you remove these?

---

### Post by dasunsrule32 on 2009-10-02
> **whoop said:**
> After the upgrade firefox reports some incompatible addons:
firefox (en) 3.0.7
Xulrunner (en) 1.9.1.2
These where probably left behind from the previous firfox.
The problem is that the enable and uninstall buttons are both disabled. So how do you remove these?

If you need them, you could always force them to work. install the add-in, nightly test tools -> then go to Addons -> Override all compatibility. Same area, lets you remove add-ons.

---

### Post by whoop on 2009-10-02
> **dasunsrule32 said:**
> If you need them, you could always force them to work. install the add-in, nightly test tools -> then go to Addons -> Override all compatibility. Same area, lets you remove add-ons.

Come again? I don't understand... I want to remove the deprecated add-ons but the enable and uninstall buttons are disabled.
Installing nightly tester tools, lets me (re-)enable or disable them again, but still not uninstall...

---

### Post by forumache on 2009-10-02
> **whoop said:**
> Come again? I don't understand... I want to remove the deprecated add-ons but the enable and uninstall buttons are disabled.
Installing nightly tester tools, lets me (re-)enable or disable them again, but still not uninstall...

Just wait. It is a know bug. They will be removed. I have them too.

---

### Post by whoop on 2009-10-02
> **forumache said:**
> Just wait. It is a know bug. They will be removed. I have them too.

Ok, cool. Is there a bugreport on launchpad? Cause I can't find it...

---

### Post by forumache on 2009-10-03
> **whoop said:**
> Ok, cool. Is there a bugreport on launchpad? Cause I can't find it...

It is this one: 
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/432556](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/432556)

---

### Post by Bert Mariën on 2009-10-03
> **whoop said:**
> After the upgrade firefox reports some incompatible addons:
firefox (en) 3.0.7
Xulrunner (en) 1.9.1.2
These where probably left behind from the previous firfox.
The problem is that the enable and uninstall buttons are both disabled. So how do you remove these?

I know what you mean!

I couldn't get it removed either.

Mind you, just this night I installed the opensuse 11.2 milestone 8, and I copied my "./mozilla folder from Ubuntu 09.04 in there. That seemed to work okay?

Than I booted into Karmic, and copied the ./mozilla folder from openSUSE 11.2 to karmic. 
Afterwards I could uninstall the depreciated add-ons.

I understand that this is not the way you want it to work, but I hope this will only be a temperary bug.

If not, we are all gonna suffer to install and reconfigure all add-ons we were use too.

Sigh!

---

### Post by whoop on 2009-10-03
> **forumache said:**
> It is this one: 
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/432556](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/432556)

Cool, cheers... and it's not even confirmed yet...

---

### Post by forumache on 2009-10-03
> **whoop said:**
> Cool, cheers... and it's not even confirmed yet...

It is "triaged" (which means it is more than confirmed, it is assigned to a developer and actively worked on).

---

### Post by whoop on 2009-10-03
> **forumache said:**
> It is "triaged" (which means it is more than confirmed, it is assigned to a developer and actively worked on).

I thought triaged meant it is being investigated with the goal to get it confirmed.

> 
Triaging bugs consists of several things:

    * Responding to new bugs as they are filed.
    * Ensuring that new bugs have all the necessary information.
    * Assigning bugs to the proper package.
    * Confirming bug reports by trying to reproduce them.
    * Setting the priority of bugs reports.
    * Searching for and marking duplicates in the bug tracking system.
    * Sending bugs to their upstream authors, when applicable.
    * Cross-referencing bugs from other distributions.
    * Expiring old bugs. 


---

### Post by forumache on 2009-10-03
> **whoop said:**
> I thought triaged meant it is being investigated with the goal to get it confirmed.

"triaged" comes after "confirmed"

There is a page with bug statuses in Launchpad, with explanation:
[http://blog.launchpad.net/general/of-bugs-and-statuses](http://blog.launchpad.net/general/of-bugs-and-statuses)
level 1 (New) is first and level 7 (Fix Released) is the latest.

---

### Post by whoop on 2009-10-03
> **forumache said:**
> "triaged" comes after "confirmed"

There is a page with bug statuses in Launchpad, with explanation:
[http://blog.launchpad.net/general/of-bugs-and-statuses](http://blog.launchpad.net/general/of-bugs-and-statuses)
level 1 (New) is first and level 7 (Fix Released) is the latest.

OK that makes sense, it's a little bit odd then that there is the line:
* Confirming bug reports by trying to reproduce them.
in [https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs) under Bug triage; as confirming a confirmed bug seems a little off.

---

### Post by forumache on 2009-10-04
> **whoop said:**
> OK that makes sense, it's a little bit odd then that there is the line:
* Confirming bug reports by trying to reproduce them.
in [https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs) under Bug triage; as confirming a confirmed bug seems a little off.

I agree with you, the meaning is a little bit distorted because of the "triage" term. Everyone can help "triaging" bugs, but only "UbuntuBugControl" team can set the Triaged status - ready for a developer to have a look at it.

Here, another page in wiki, better explained than the previous one:
[https://wiki.ubuntu.com/Bugs/Status](https://wiki.ubuntu.com/Bugs/Status)

---

### Post by QQi on 2009-10-05
try this!

sudo rm -rf /usr/lib/firefox-addons/extensions/langpack*
sudo rm -rf /usr/lib/xulrunner-addons/extensions/langpack*

---

### Post by QQi on 2009-10-05
* sorry double post

---

### Post by dino99 on 2009-10-05
> **QQi said:**
> try this!

sudo rm -rf /usr/lib/firefox-addons/extensions/langpack*
sudo rm -rf /usr/lib/xulrunner-addons/extensions/langpack*

thanks  :P

---

