---
title: "Beta installer still says Software Store"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Copernicus1234 on 2009-10-03
I just want to let any Ubuntu dev know this since its easy to miss. The installer slide show picture about installing programs still says Software Store even though the application has been renamed to Software Center.



Also I think its not wise to have the software center pre-installed in Karmic. Its not ready. Here is my reasons for this statement:

- When picking a main category such as Games or any other, you get a list of applications with no means of knowing which ones are good or bad. If you are new to Ubuntu, you will not have any idea of what applications to try first. There is a big chance that people will randomly select something crappy and think all Ubuntu apps are worthless. How are they supposed to find the good stuff?

- It looks ugly at this point in time.

- The navigation is quite frustrating. I spent a few minutes with it but got annoyed and went back to Synaptic. Im sure it will improve, but right now its clearly a sign of programmers designing the interface. Its logical but not user friendly.

---

### Post by woodbj on 2009-10-03
> **Copernicus1234 said:**
> I just want to let any Ubuntu dev know this since its easy to miss. The installer slide show picture about installing programs still says Software Store even though the application has been renamed to Software Center.

[https://lists.ubuntu.com/archives/karmic-changes/2009-October/009954.html](https://lists.ubuntu.com/archives/karmic-changes/2009-October/009954.html)

> [ Dylan McCall ]
  * Changed "Software Store" to "Software Center" since it has been renamed.

  [ Evan Dandrea ]
  * Updated translations from Launchpad.


---

### Post by vishalrao on 2009-10-03
Yup, fixed: [https://launchpad.net/ubuntu/karmic/+source/ubiquity-slideshow-ubuntu/8](https://launchpad.net/ubuntu/karmic/+source/ubiquity-slideshow-ubuntu/8)

---

### Post by zekopeko on 2009-10-03
> **Copernicus1234 said:**
> The navigation is quite frustrating. I spent a few minutes with it but got annoyed and went back to Synaptic. Im sure it will improve, but right now its clearly a sign of programmers designing the interface. Its logical but not user friendly.

This made me laugh so hard :lolflag:
Read the wiki spec and  then try saying that the interface was designed by a programmer.

---

### Post by infamousrev on 2009-10-03
> **Copernicus1234 said:**
> 
- The navigation is quite frustrating. I spent a few minutes with it but got annoyed and went back to Synaptic. Im sure it will improve, but right now its clearly a sign of programmers designing the interface. Its logical but not user friendly.


Actually I found the user interface improved. For someone who is not used to synaptic it looks way more attractive and its much more intuitive.

I never got used to synaptic because I use apt-get and aptitude for everything, but looking at your statements your a trained synaptic user.

---

### Post by mpt on 2009-10-03
Thanks for your feedback on the Ubuntu Software Center.

> **Copernicus1234 said:**
> - When picking a main category such as Games or any other, you get a list of applications with no means of knowing which ones are good or bad. If you are new to Ubuntu, you will not have any idea of what applications to try first. There is a big chance that people will randomly select something crappy and think all Ubuntu apps are worthless. How are they supposed to find the good stuff?

The same is true for the utility the Software Center is replacing, Add/Remove Applications. Add/Remove does show [popularity contest]("http://popcon.ubuntu.com/") data, but that is heavily biased towards applications that are installed by default, and may also be biased towards geekier software because it requires people to opt in in an obscure place.

In version 2.0, we plan to introduce ratings and reviews for applications and other packages. We’re also [inviting your suggestions]("https://wiki.ubuntu.com/SoftwareCenter/Classification") on how to subcategorize (and recategorize) the applications, so that it’s easier to find (for example) games of a particular type.

> *- It looks ugly at this point in time.*

Do you have any suggestions on how to make it more beautiful? Mockups welcome.

> *- The navigation is quite frustrating. I spent a few minutes with it but got annoyed and went back to Synaptic. Im sure it will improve, but right now its clearly a sign of programmers designing the interface. Its logical but not user friendly.*

I’m assure you, programmers did not design the interface. ;) Can you give a specific example of something that frustrated you? I plan to do user testing (or, to reduce bias, to get someone else in the Design team to do user testing!) on the Center early in the Lucid cycle. Is it easy for people to get back to the screen they were on previously? Maybe we need Back and Forward buttons. Is the distinction between search results and other screens obvious enough? Maybe search results need their own segment in the path button. Things like that.

---

### Post by Copernicus1234 on 2009-10-03
> **mpt said:**
> 
I’m assure you, programmers did not design the interface. ;) Can you give a specific example of something that frustrated you? I plan to do user testing (or, to reduce bias, to get someone else in the Design team to do user testing!) on the Center early in the Lucid cycle. Is it easy for people to get back to the screen they were on previously? Maybe we need Back and Forward buttons. Is the distinction between search results and other screens obvious enough? Maybe search results need their own segment in the path button. Things like that.

Ok. :)

I will get back to this thread soon with a more detailed list of suggestions for changes to the application. Or perhaps start a new thread on it.

Me using the app for 5 minutes is probably not enough to make a fair judgment of it so I will spend more time with it before commenting as well. :)

---

### Post by forcecore on 2009-10-03
Someone has forgotten add/remove still in ubuntu???

---

### Post by MadsRH on 2009-10-03
> **mpt said:**
> Thanks for your feedback on the Ubuntu Software Center....Do you have any suggestions on how to make it more beautiful? Mockups welcome...

I would like to see the blue background tweaked. Perhaps just a gradient? 


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=129303&d=1253559003[/IMG]

---

### Post by tom56 on 2009-10-03
I disagree with the OP. I reckon that Software Centre is a massive improvement over Add/Remove Apps. It is cleaner and easier to find your way around. I think the screenshots are and overall it's just less intimidating. I agree work needs to be done, I'm looking forward to ratings and I think that despite the improvements more could be done regarding the size of the categories. "Internet" covers hundreds of possible scenarios. However, it's all very much a step in the right direction. The increase in responsiveness has finally made it suitable for day-to-day use in a way that Add/Remove never was.

---

### Post by Copernicus1234 on 2009-10-03
Im starting another thread about the Software Center soon (or posting in the [existing thread]("http://ubuntuforums.org/showthread.php?t=1280641") about it) so lets not discuss it here any more. :)

Im setting the thread as Solved.

---

### Post by Mr. Picklesworth on 2009-10-03
Hey, quick question about Software Center, while we are here :)
Is it still using an index file of its own to decide which apps to list (which I think gnome-app-install did), or is it picking through all the available stuff like PackageKit does?

---

### Post by exploder on 2009-10-03
I like the fact that the Software Center opens doors for game development for Linux. There is room for improvement to the interface but agree that this is a huge step in the right direction.

---

### Post by Seventh Reign on 2009-10-03
I have to disagree with the OP (what exactly does that stand for anyway?) too.  The whole point of having it installed and running by default is so that we can TEST it and suggest the additions/changes that will make it better.  If its not installed, it wont be tested, therefore it will never become any better.  

Remember its not 'just' a few select Linux geeks thats test all the Alpha/Beta apps and send in their suggestions.  Its pretty much every person that logs into a GNU/Linux based PC.  Atleast all the people that actually care about improving GNU/Linux.

On a side note, I would get rid of that Blue background altogether.  It just doesnt match and looks gaudy.

---

### Post by mpt on 2009-10-03
> **forcecore said:**
> Someone has forgotten add/remove still in ubuntu???

If Add/Remove is still installed when you upgrade from 9.04 to 9.10 beta, please report a bug.

> **MadsRH said:**
> I would like to see the blue background tweaked. Perhaps just a gradient?

[Previously]("http://ubuntuforums.org/showthread.php?p=7986221#post7986221"). I’m sure there are many more beautiful things we can do with the main screen. (For example, a department button doesn’t need to consist *solely* of the category icon.)

> **Mr. Picklesworth said:**
> Is it still using an index file of its own to decide which apps to list (which I think gnome-app-install did), or is it picking through all the available stuff like PackageKit does?

It’s still using the [app-install-data-ubuntu]("https://launchpad.net/ubuntu/+source/app-install-data-ubuntu") package. We will need to find a better solution before version 3, though. app-install-data-ubuntu knows only about Main and Universe, but we want applications in PPAs to have human-readable names, icons, categories, screenshots and so on as well.

---

### Post by zekopeko on 2009-10-03
> **mpt said:**
> [Previously]("http://ubuntuforums.org/showthread.php?p=7986221#post7986221"). I’m sure there are many more beautiful things we can do with the main screen. (For example, a department button doesn’t need to consist *solely* of the category icon.)

That still doesn't mean that having a gradient like MadsRH suggested isn't an improvement. That hardcoded color is not the best of choices.
And I agree that the Department screen (why not just call it categories?) should be more like a web page. Perhaps featured apps and a tag cloud etc?

> It’s still using the [app-install-data-ubuntu]("https://launchpad.net/ubuntu/+source/app-install-data-ubuntu") package. We will need to find a better solution before version 3, though. app-install-data-ubuntu knows only about Main and Universe, but we want applications in PPAs to have human-readable names, icons, categories, screenshots and so on as well.

I think that this would be a perfect example when to talk to Debian and see if something can be done in this regard via a shared spec.

---

### Post by forcecore on 2009-10-04
> **mpt said:**
> If Add/Remove is still installed when you upgrade from 9.04 to 9.10 beta, please report a bug.

There is nothing to report even current daily has Add/Remove in System>Preferences. Please check Ubuntu install developer desk and maybe there is some bamboo moonshine bottle :-k

SRY: did not notice that is solved topic....

---

### Post by MadsRH on 2009-10-04
> **mpt said:**
> ...[Previously]("http://ubuntuforums.org/showthread.php?p=7986221#post7986221"). I’m sure there are many more beautiful things we can do with the main screen. (For example, a department button doesn’t need to consist *solely* of the category icon.)...

I'm sorry - I had not seen your first reply :oops:

---

