---
title: "Time To Drop AppArmor And Use SELinux"
date: 2008-07-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-07-24
SELinux was always the superiour solution.

Novell sacked all of its AppArmor team in 2007.

I think its time Ubuntu went SELinux.

Do people agree?

---

### Post by amano on 2008-07-24
No. Because you don't give any technical reasons to switch the framework.

*The fact that there is not an appamour team at Novell anymore doesn't mean that it isn't still supported by the community. Why do you need an apparmor team at Novell? SELinux isn't driven by Novell either.
*The main advantage of apparmor is its ease of use (compared to SELinux). 
*"Superior" is a strong word, but doesn't mean anything in technical terms. What do you want to achieve that SELinux can do and apparmor cannot?

Thus until more detailed technical reasons are given, the  development resources should be spent otherwise. Do people agree? :lolflag:

---

### Post by TimothyLuke on 2008-07-24
My personal preference is for AppArmor over SELinux as it doesnt require any changes to the applications or kernel.  I can use the same kernel as a non AppArmor installation, I can use the same application base.  

I run a server farm where all the binary apps are located on a NIS share.  The servers are currently configured where some use AppArmor others dont but they all share the same binary base.

---

### Post by Nullack on 2008-07-25
Have a read of linux magazine issue 69 which has a comprehensive look at selinux and apparmor.

---

### Post by litemotiv on 2008-07-25
> **Nullack said:**
> Have a read of linux magazine issue 69 which has a comprehensive look at selinux and apparmor.

geez, is it also possible to give negative thanks on this forum?

---

### Post by ajackson on 2008-07-25
> **Nullack said:**
> Have a read of linux magazine issue 69 which has a comprehensive look at selinux and apparmor.

OK but to quote Amano:

> *The fact that there is no appamour team at Novell anymore doesn't mean that it isn't still supported by the community. Why do you need an apparmor team at Novell? SELinux isn't driven by Novell either.
*The main advantage of apparmor is its ease of use (compared to SELinux).
*"Superior" is a strong word, but doesn't need anything in technical terms. What do you want to achieve that SELinux can do and apparmor cannot?

Because a magazine doesn't like it is not a good enough reason, there are linux magazines that are anti KDE/Gnome (delete as appropriate), should they be scrapped because of the magazines view?

---

### Post by Nullack on 2008-07-25
The fact its in a magazine is irrelevant. Its a comprehensive look at the two solutions.

---

### Post by PmDematagoda on 2008-07-25
> **Nullack said:**
> The fact its in a magazine is irrelevant. Its a comprehensive look at the two solutions.

Perhaps you could give us a link to the magazine without just pointing at the particular magazine?

About Apparmor and SELinux, I respect both of them in different ways, I believe that there are places where Apparmor is better than SELinux and places where SELinux is better than Apparmor, but if it came down to a choice between the two, I would choose Apparmor since overall it is more easier to configure than SELinux is, although I am currently taking a good look at SELinux as well.

And Apparmor isn't dead, there are new releases of Apparmor coming in, 2.3 beta is out and there are patches for the new kernels, so it is not dead.

---

### Post by ajackson on 2008-07-25
> **Nullack said:**
> The fact its in a magazine is irrelevant. Its a comprehensive look at the two solutions.
Well I've seen comprehensive looks at the differences (and similarities) between KDE and Gnome, so my question still stands should one of them go?

What you seem to fail to grasp is that Linux is about choice, the Ubuntu team have chosen to use AppArmour and it is doing a good job, other distros choose SELinux (Fedora I think is one) and guess what, that is doing a good job as well. Guess what again Ubuntu also carries SELinux (well I just checked in the Hardy reps and it is there), so you can choose to use SELinux rather than AppArmour.

Simple really, the choice is there.

---

### Post by Gina on 2008-07-25
Seems to me the old addage "if it ain't broke, don't fix it" applies.  There must be a good reason to change otherwise it's wasting effort that could be better spent elsewhere.

---

### Post by Nullack on 2008-07-25
> **ajackson said:**
> What you seem to fail to grasp is that Linux is about choice, the Ubuntu team have chosen to use AppArmour and it is doing a good job, other distros choose SELinux (Fedora I think is one) and guess what, that is doing a good job as well. Guess what again Ubuntu also carries SELinux (well I just checked in the Hardy reps and it is there), so you can choose to use SELinux rather than AppArmour.

Simple really, the choice is there.

I suggest your arguments arent fully considered on this topic. :)

* By making AppArmor default, thats the supported configuration that many people will use accepting the architectural decision made by Canonical for them. In this case, users of this type done want choice they want it to be secure and just work. Keeping in mind the Ubuntu philosophy of having one supported method for doing things.
* Having SELinux in the repos is not the same as having it supported by default.
* A large part of AppArmor and SELinux is the profile, and Canonicals decision for AppArmor has watered down the strength of SELinux out of the box from the repos. A serious security user will face an unnecessarily lengthy episode to get the profile up to standard.

As for the comments about AppArmor being a suitable solution I think reflects a lack of understanding of the issues with security.

The comments about gnome/kde are red herrings to this debate. Whats more, the situation with different desktops is that we have child distros like Kubuntu and others that specifically allow for an easy adoption. Kubuntu is a poor KDE example but thats another topic in itself as a red herring to this topic.

---

### Post by amano on 2008-07-25
> **Nullack said:**
> 
As for the comments about AppArmor being a suitable solution I think reflects a lack of understanding of the issues with security.

Sure. We should have honored your security knowledge and expertise in the first place. Please forgive us our blasphemy and make our lives more secure from above.

> **Nullack said:**
> 
The comments about gnome/kde are red herrings to this debate.

What debate? There isn't any technical debate. Just some ranting from your site that you think that apparmor might not be secure enough for you.

---

### Post by Nullack on 2008-07-25
Amano you need to learn how to discuss things properly. Your making the fallacy of ad hominem, which apart from doing nothing to prove your position shows an ugly tendency to unnecessarily abuse others who dont agree with your position.

Opinions with which you disagree are not rants.

Try to be calm, please :)

---

### Post by Riffer on 2008-07-25
Ok as a noob what the heck is apparmour/SELinux?

---

### Post by loell on 2008-07-25
> **Riffer said:**
> Ok as a noob what the heck is apparmour/SELinux?

simply google it ;), there are more articles out there than just to try to explain it concisely here.

---

### Post by PmDematagoda on 2008-07-25
> **Nullack said:**
> Amano you need to learn how to discuss things properly. Your making the fallacy of ad hominem, which apart from doing nothing to prove your position shows an ugly tendency to unnecessarily abuse others who dont agree with your position.

Opinions with which you disagree are not rants.

Try to be calm, please :)

I'm sorry, but you are not making much sense either, you say that Apparmor should be dropped in favour of SELinux, but the reasons you gave in your previous posts are not really enough to warrant the removal since:-
1) Apparmor is not dead, new releases of it and patches for the newer kernels are still coming out.

2) You say that "SELinux was always the superior choice", what evidence do you have to support this?

---

### Post by Nullack on 2008-07-25
The magazine article is available on the web if you google it, rather than regurgitate all of it here.

---

### Post by PmDematagoda on 2008-07-25
> **Nullack said:**
> The magazine article is available on the web if you google it, rather than regurgitate all of it here.

Did you note the date of the magazine by any chance? It is almost 2 years old, this may mean that the points raised in that magazine have been invalidated by new releases of SELinux and Apparmor. Perhaps you have a newer resource for us to read and then make a decision?

For the people wanting the magazine article, it is in PDF, it can be found [here]("http://w3.linux-magazine.com/issue/69/AppArmor_vs_SELinux.pdf").

---

### Post by Nullack on 2008-07-25
The Linux kernel mailing list has had extensive discussions on SELinux vs AppArmor. Linus became frustrated on a number of times with these sorts of dicussions and ended up becoming irate (as he does) with saying that security people were "******* around with their opinions" in reference to the difficulty he was having in discerning NSA supporters vs Novell supporters. Still, I think its fair to say that the "general" opinion on the linux kernel mailing list is that SELinux is the strongest solution but is a hassle to configure.

Can I add that if SELinux was the default in Ubuntu then the weight behind it would pretty soon end up in a good profile thats largely hassle free for the end user. The profiles really are key.

The date issue of the article isnt so important as the basic approach of both methods hasnt really changed.

---

### Post by PmDematagoda on 2008-07-25
You say that profiles are the key in SELinux effectiveness, but the fact is that the profiles are the keys in both SELinux and Apparmor, if you have rubbish profiles for both Apparmor or SELinux then the protection provided by the both of them will be rubbish or over much. 

So the end result is that both security systems are good in some way or the other, each one has their own specific applications at which they excel, but the fact is that there isn't any evidence to prove that SELinux is really miles better than Apparmor, and vice versa as well. So why would Apparmor be dropped in favour of SELinux if the Ubuntu developers are comfortable with using Apparmor and that there aren't any dangerous/potentially harmful issues with Apparmor?

---

### Post by Nullack on 2008-07-26
* SELinux has the ability for more fine grained control and hence the issue of complexity
* SELinux has a larger and more active ecosystem around it in comparison to AppArmor which is declining
* SELinux is generally seen as the more secure solution, acknowledging the difficulty in actually measuring this
* Existing profiles exist in other distros as a launching pad for Ubuntu improving the selinux profile

Yes, ofcourse both use profiles. However my point was that good profiles can result in the complexity of selinux being hidden from the end user.

---

### Post by PmDematagoda on 2008-07-26
> **Nullack said:**
> Yes, ofcourse both use profiles. However my point was that good profiles can result in the complexity of selinux being hidden from the end user.

That is true, right until you get to an AVC denial where you need to figure out what on earth to do, while the SETroubleshooter is well made, there is no way to be sure if the solutions it is suggesting is good, or if the AVC denial is occurring only due to a bug which has happened before, especially in the first few weeks of the Fedora 9 release. The fact is that no matter how well you make a profile, there is always some place where the profile does not cover or is not supposed to cover in the interests of security.

> 
* SELinux has a larger and more active ecosystem around it in comparison to AppArmor which is declining
How is the Apparmor community declining, examples please?

> * SELinux is generally seen as the more secure solution, acknowledging the difficulty in actually measuring this
Yes it is, but in this current world I would think that a normal desktop user would want an easy to use security solution than a very complex yet powerful security solution, and the fact is that Apparmor provides quite a lot even though it is very simple.

---

### Post by ajackson on 2008-07-26
> **Nullack said:**
> * SELinux has a larger and more active ecosystem around it in comparison to AppArmor which is declining
Care to link to your evidence to back up this "fact"?

> * SELinux is generally seen as the more secure solution, acknowledging the difficulty in actually measuring this
Peoples opinions are not facts, they are opinions. Of course pro SELinux people would say SELinux was more secure just as pro AppArmour people will say the same about AppArmour. Without facts to back them up opinions aren't really a valid argument for which is better.

> * Existing profiles exist in other distros as a launching pad for Ubuntu improving the selinux profile
Other distros could use Ubuntus existing AppArmour profiles to improve their AppArmour profiles. It's exactly the same argument as you posed with SELinux and AppArmour swapped.

Also who is to say that Ubuntus SELinux profiles aren't pretty good anyway? Just because it's not default doesn't automatically make it rubbish.

It seems SELinux and AppArmour are becoming the new KDE and Gnome, both do the job and both are the best according to their relative supporters.

Basing an argument on a two year old magazine article which is basically two peoples opinions (with the writer chipping in his opinion at the end) does not lead to a firm set of facts for a fairly major change in development.

Edit to add:

> As for the comments about AppArmor being a suitable solution I think reflects a lack of understanding of the issues with security.
Again you have evidence to back up the fact about it not being a suitable solution do you? Are you really suggesting that the security experts who work on Ubuntu don't have a clue?

I understand security issues very well thank you, I also understand that opinion does not equal fact.

---

### Post by olskar on 2008-07-26
A word from Shuttleworth about this:

> derStandard.at: Speaking about security, are you going to stay with AppArmor now that Novell has dropped the ball on it or are you going to change over to SELinux?

Shuttleworth: That's a very interesting question. There's certainly been a lot of change there. But that's one of the tricky things when managing the evolution of a platform, you are taking a leap of faith on certain communities. Especially with communities which are largely driven by other companies there's a real risk with that, cause they might just send their strategy.

---

### Post by Nullack on 2008-07-26
Mark is right - obviously when architectural decisions are made about Ubuntu that are primarily driven by other companies there is risk. In the case of AppArmor, this risk came to fruition.

Unlike AppArmor, the NSA continue to fund paid developers for this code.

For those people who want a detailed answer (pages worth) of why and how SELinux offers a more fine grained secure solution than AppArmor, they really should look at the linux kernel mailing lists threads. It boils down to the NSA's approach being more fine grained, but in turn that comes with additional complexity. Im happy to discuss specific points of contention raised in the LKML.

cheers

---

### Post by Astinus on 2008-07-26
> **Nullack said:**
> Unlike AppArmor, the NSA continue to fund paid developers for this code.

For those people who want a detailed answer (pages worth) of why and how SELinux offers a more fine grained secure solution than AppArmor, they really should look at the linux kernel mailing lists threads. It boils down to the NSA's approach being more fine grained, but in turn that comes with additional complexity. Im happy to discuss specific points of contention raised in the LKML.


But you're clearly not willing to answer other questions posed by forum members demanding examples of how the AppArmor community is declining. Hilarious. Nobody has mentioned the other alternatives like grSecurity or RSBAC either. Both are viable and actively developed.

---

### Post by Nullack on 2008-07-26
Ive already addressed that point - Novell sacked their entire AppArmor team. The response was "its still community supported". Obviously having paid full time developers, which the NSA continue to do with SELinux, results in more current code. Its certainly not a case of me being unwilling to answer questions - its more that some of you arent interested in a fair dinkum discussion and want to troll.

I'll introduce another example - if you were to explore the Linux kernel mailing lists which I am encouraging people to do, you would see the time taken for example to get AppArmor supported in linux kernel 2.6.26 against SELinux is very much different.

There's smack too to your list. I am not closely familiar with these others, and if you consider them to be better unlike some other blinkered people here I am interested in you referring me to some material so I can explore those. So far, SELinux has the most fine grain control Ive seen.

---

### Post by loell on 2008-07-27
wouldn't  it be better that you make a [blueprint]("https://blueprints.launchpad.net/") 

prove your points there "specifically" , that way , you won't  be wasting your time here introducing your proposal which you feel so strongly.


edit--

oh!! [https://blueprints.launchpad.net/ubuntu/+spec/selinux-by-default]("https://blueprints.launchpad.net/ubuntu/+spec/selinux-by-default")

looks like there is one already..

---

### Post by indecisive on 2008-07-27
Can both be used?

---

### Post by indecisive on 2008-07-27
Can both be used?
-edit-
Pardon me for repeating my message -- I forgot to refresh another Firefox window.

---

### Post by ajackson on 2008-07-27
> **Nullack said:**
> Obviously having paid full time developers, which the NSA continue to do with SELinux, results in more current code.
Microsoft pay developers do they not? Where you get the idea that because something is developed by the community therefore it is rubbish I don't know.

> Its certainly not a case of me being unwilling to answer questions - its more that some of you arent interested in a fair dinkum discussion and want to troll.
No-one is trolling, asking you to back up your claims with evidence is not trolling. The fact that you seem so unwilling to back up any of your claims however leads to the assumption you have no evidence.

> I'll introduce another example - if you were to explore the Linux kernel mailing lists which I am encouraging people to do, you would see the time taken for example to get AppArmor supported in linux kernel 2.6.26 against SELinux is very much different.
Different in what way? Longer? Shorter? Can time taken to implement something be an accurate guideline of how good something is (Vista anyone? Or if you are in the UK the Millenium Dome?)

> There's smack too to your list. I am not closely familiar with these others, and if you consider them to be better unlike some other blinkered people here I am interested in you referring me to some material so I can explore those. So far, SELinux has the most fine grain control Ive seen.
You ask for evidence about other solutions but are unwilling to produce any to back up your own, that is hypocritical. Then to start using emotive terms like blinkered people tends to suggest you are now doing what you have accused others of, trolling.

I have never said AppArmour is better or worse than SELinux, the fact that even after Novell dropping it's AppArmour team the developers of Ubuntu are happy to continue to use AppArmour suggests that it isn't a terrible product.

You also failed to address my point about how good the SELinux profiles that Ubuntu have are (I don't know myself), for all I (and you) know they could be as good as a distro that uses SELinux by default. The fact remains you do not know or (again) have provided no evidence to prove that they are worse.

Opinions are fine, everyone has one and everyone is entitled to theirs but to persuade the development team to change you need hard cold facts not maybes.

---

### Post by RAOF on 2008-07-27
> **Nullack said:**
> ...
For those people who want a detailed answer (pages worth) of why and how SELinux offers a more fine grained secure solution than AppArmor, they really should look at the linux kernel mailing lists threads. It boils down to the NSA's approach being more fine grained, but in turn that comes with additional complexity. Im happy to discuss specific points of contention raised in the LKML.


Finer grained control does not necessarily imply better.  In particular, it doesn't necessarily imply better for all use-cases.

Sadly I don't have citations, but my general impression over the course of my mailinglist browsing has been that SELinux is, or can be, more secure than AppArmour, but this comes at the cost of significantly higher setup costs and ongoing problems.  For example, the SELinux profile in Fedora 9 appears to be breaking iPod support in Banshee now.  AppArmour, while apparently less of a security win, seems good enough for the desktop, and doesn't appear to have the same problems with accidental breakage.

Note that we also have a suite of SELinux policies for Ubuntu; if you want/need the protection, they're available in the archives.  AppArmour seems a better choice for the desktop, though.

---

### Post by Nullack on 2008-07-27
The Common Criteria for Information Technology Security Evaluation is a security standard. SELinux has EAL4+ certification where I understand AppArmor does not.

Given how time consuming it is to evaluate different security modules for LSM, this alone is reason enough for some companies not to use AppArmor ontop of Novell sacking it's AppArmor team.

RAOF thats the true situation - SElInux offers more ways to be secure than AppArmor but that comes at the expense of needing a really good profile for it to be seamless to the end user. As I contended in earlier posts I think the greater weight behind Ubuntu can result in a better desktop profile than Fedora. People asking for evidence as to why SELinux is more fine grained really need to educate themselves from the LKML and the book "SELinux by Example" which is a comprehensive text on SELinux.

As for Ubuntu servers, I think having a solid SELinux profile would give the assurance of common criteria for companies making deployment decisions. Having strong server security would be a key feature for having more Ubuntu servers over Novell servers. Red Hat already differentiate themselves from Novell with their certifications.

---

### Post by RAOF on 2008-07-28
> **Nullack said:**
> ...
RAOF thats the true situation - SElInux offers more ways to be secure than AppArmor but that comes at the expense of needing a really good profile for it to be seamless to the end user. As I contended in earlier posts I think the greater weight behind Ubuntu can result in a better desktop profile than Fedora....
I'm unconvinced that we actually *have* a greater weight than Fedora.  Regardless, SELinux seems like an extremely high-maintenance solution; you'll need to update it everytime an application starts accessing different resources, etc.  Add to that the significantly lower need for this sort of invasive security measure on a desktop, and I don't think you've presented a compelling case for any switch.  *On the desktop*.  On the server we have selinux profiles anyway.

The productive way of moving this forward on your part would probably include demonstrating a desktop SELinux profile for Ubuntu, or how it could reasonably be created/maintained by the existing developers.

> **Nullack said:**
> 
As for Ubuntu servers, I think having a solid SELinux profile would give the assurance of common criteria for companies making deployment decisions. Having strong server security would be a key feature for having more Ubuntu servers over Novell servers. Red Hat already differentiate themselves from Novell with their certifications.

We already have a solid SELinux profile, though.  Just because it isn't enabled by default on our desktops, doesn't mean that it doesn't exist.  Again: it seems that SELinux probably makes sense *on a server*.  But a server both requires substantially better security measures and is substantially less complex than a desktop.

---

### Post by almostlinux on 2008-07-28
> **Riffer said:**
> Ok as a noob what the heck is apparmour/SELinux?

  Another one of those 'religious flame war' contenders.

---

### Post by Nullack on 2008-07-28
A better answer is that there is various Linux Security Modules. Previously Linux did not allow for fine grained security control and this was inadequate for a real operating system. This is what these LSMs do with using things like mandatory access control. Various solutions have come about and Ubuntu by default uses AppArmor.

---

### Post by ajackson on 2008-07-28
> **Nullack said:**
> The Common Criteria for Information Technology Security Evaluation is a security standard. SELinux has EAL4+ certification where I understand AppArmor does not.
Is that because AppArmour has not been tested or because you can not find the results? Out of curiosity what certification do things like windows kernal and firewall hold? (I don't know personally).

I assume SELinux **had** to be tested to meet funding guidelines for the NSA.

> Given how time consuming it is to evaluate different security modules for LSM, this alone is reason enough for some companies not to use AppArmor ontop of Novell sacking it's AppArmor team.
Another claim not backed up by evidence, so I'll take it as your opinion.

> People asking for evidence as to why SELinux is more fine grained really need to educate themselves from the LKML and the book "SELinux by Example" which is a comprehensive text on SELinux.
Erm maybe learn a bit of reading comprehension? People have been asking for evidence to back up your facts about AppArmour being in decline, as far as I recall no-one was doubting that SELinux is capable of doing the job it is defined for.

> Red Hat already differentiate themselves from Novell with their certifications.
If by certifications you mean being a certified RH admin (and whatever other certifications they have) then while helpful for obtaining employment I wouldn't say they are that highly rated (note this is my opinion, I'm not stating it as a fact).

Coming back to even more of my questions that you won't (can't?) answer:

Does not having paid developers make something rubbish?
How do Ubuntu's SELinux profiles compare with others?
Does time to implement something really count as a guide to how good something is? (Another recent example would be Age of Conan).

---

### Post by PmDematagoda on 2008-07-29
> **indecisive said:**
> Can both be used?

It is possible, but the results are likely to be very, very messy.

---

### Post by Nullack on 2008-07-29
Does not having paid developers make something rubbish?

* No, but in this case it has taken away some skilled developers of the original company (that stayed on with Novell) that Novell bought, Open Sourced and then sacked. In this particular case alot of expertise has gone out the door. Some of these people are advertising themselves now as "Linux Mercenaries" but we will see how well that goes in terms of their volunteer contributions to AppArmor.

* If you compare the number of commits into AppArmor since we had paid specialists on the project you will see it has actually dropped - there is a clear pattern here.

How do Ubuntu's SELinux profiles compare with others?

* I'm not at this stage wanting to answer this question (in relation to Desktops) because I have not spent enough time with Ubuntu's and Fedora's default profiles. I think answering it now wouldnt do the situation justice. I will offer my opinion when I have a mature one.

* I've seen most enterprises want to deploy their own profile (which might be based off another) and want to lock everything down except for the specific service the server is for.

Does time to implement something really count as a guide to how good something is? (Another recent example would be Age of Conan).

* Again no, but I think the reduction in commits from AppArmor and the project taking a long time to keep up to date relative to other alternatives is one indication of the decline in AppArmor.

* What I was referring to here with my original point is I've seen many companies not wanting to look into security alternatives that are not certified. There is significant cost involved in security certifications and this is one of the key reasons why I have seen SELinux (RHEL) be deployed over Novell because Red Hat has EAL4+ certification - AppArmor does not have this certification.

Erm maybe learn a bit of reading comprehension? People have been asking for evidence to back up your facts about AppArmour being in decline, as far as I recall no-one was doubting that SELinux is capable of doing the job it is defined for.

* People were also not willing to agree that AppArmor did not offer the same level of granularity tan what SELinux has. Thankfully we had some experienced people come along and reinforce the fact that actually yes, SELinux has more fine grained control than AppArmor albeit at the expense of more complexity. Some people then tried to make me re-invent the wheel by citing all the reasons why this is so.....Simply, the Linux Kernel Mailing List and the book I referenced can provide comprehensive answers over hundreds of pages why this is so. There is no serious security professional who would try to claim that AppArmor can lock down all things SELinux can. This is why SELinux is a more secure solution than AppArmor.

On another note however Ive been looking at RSbac and there is some nice bits being committed into their tree. Competition is good and its going to be exciting how this turns out in the months ahead.

---

### Post by PmDematagoda on 2008-07-29
Using the number of commits to enforce the fact that the Apparmor community is declining is not really valid since the number of bugs in Apparmor may just be reducing(hence the decreasing commits), obviously almost any application would have a high number of commits at the time of it's inception.

> * People were also not willing to agree that AppArmor did not offer the same level of granularity tan what SELinux has. Thankfully we had some experienced people come along and reinforce the fact that actually yes, SELinux has more fine grained control than AppArmor albeit at the expense of more complexity. Some people then tried to make me re-invent the wheel by citing all the reasons why this is so.....Simply, the Linux Kernel Mailing List and the book I referenced can provide comprehensive answers over hundreds of pages why this is so. There is no serious security professional who would try to claim that AppArmor can lock down all things SELinux can. This is why SELinux is a more secure solution than AppArmor.

It is a widely known fact that SELinux can enforce more granular control than Apparmor can, you may point to people(like me) who questioned your statement that "SELinux was always the more superior choice", but the fact is that when you consider everything about both systems such as:-
1) Ease of use.
2) Flexibilty.
3) Security.
4) Efficient use of resources.
then both SELinux and Apparmor are on the same level because they lack something, SELinux lacks:-
1) Ease of use.
2) Efficient use of resources(not much on this).
while Apparmor is the complete opposite(but not much either).

For a system like Ubuntu(especially the desktop version), having SELinux and tuning it to the desktop needs would be absolute hell, even Fedora took a very, very long time to do so and it still isn't complete either, you would say that the combined efforts of both Ubuntu and Fedora will make the task easier, it may make it easier but since not everyone here is a good SELinux administrator(most don't even know what SELinux is) it won't be that faster either. And let me ask you a question, how long did you take to be proficient in SELinux(i.e. learn to create proper profiles, proper SELinux administration, etc)?

---

### Post by Nullack on 2008-07-29
You make some good points there, and I earlier stated that I felt the increased weight behind Ubuntu would eventually lead to a robust desktop profile in Ubuntu.

Lets however for a moment just look at it from Canonicals point of view. We should be able to accept that more servers running Ubuntu server is good for their business right? So:

* EAL4+ certification would be an added feature to the marketing of Ubuntu server and further strengthen the product. This would match Red Hats certification here too.
* Ubuntu server could be additionally value added by shipping it with server roles profiles using SELinux custom tailored for typical server roles. Improve on what Red Hat supplies, to position Ubuntu ahead of Red Hat ontop of already existing things like better package management.
* Canonical can add additional profit in consulting fee's for customers who dont want to deal with the project of doing additional custom profiles for their boxes. Before people accuse me of suggesting vendor lock in, customers could choose to use another LSM, another service provider and so on.

Or, perhaps Canonical chooses to do nothing right now, and wait / help RSbac to be a terrific product, and go with that when its ready.

---

### Post by PmDematagoda on 2008-07-29
> **Nullack said:**
> You make some good points there, and I earlier stated that I felt the increased weight behind Ubuntu would eventually lead to a robust desktop profile in Ubuntu.

Lets however for a moment just look at it from Canonicals point of view. We should be able to accept that more servers running Ubuntu server is good for their business right? So:

* EAL4+ certification would be an added feature to the marketing of Ubuntu server and further strengthen the product. This would match Red Hats certification here too.
* Ubuntu server could be additionally value added by shipping it with server roles profiles using SELinux custom tailored for typical server roles. Improve on what Red Hat supplies, to position Ubuntu ahead of Red Hat ontop of already existing things like better package management.
* Canonical can add additional profit in consulting fee's for customers who dont want to deal with the project of doing additional custom profiles for their boxes. Before people accuse me of suggesting vendor lock in, customers could choose to use another LSM, another service provider and so on.

Or, perhaps Canonical chooses to do nothing right now, and wait / help RSbac to be a terrific product, and go with that when its ready.

If you are talking about market share, then what about Novell's SLES? Novell still uses Apparmor in SLES instead of SELinux(they still promote it). And since Novell is a commercial company, I don't think they would want to waste money or just watch themselves deteriorate by using an "inferior security system" like Apparmor.

> 
* Ubuntu server could be additionally value added by shipping it with server roles profiles using SELinux custom tailored for typical server roles. Improve on what Red Hat supplies, to position Ubuntu ahead of Red Hat ontop of already existing things like better package management.
This requires people skilled in SELinux, people need to be trained and it isn't that easy. Red Hat's chief SELinux engineer, Dan Walsh still doesn't know everything about SELinux(after years of working with it) and even he makes mistakes, so imagine how hard SELinux newbies would find it.

> Or, perhaps Canonical chooses to do nothing right now, and wait / help RSbac to be a terrific product, and go with that when its ready.
Perhaps, but I haven't seen any news of it, let alone heard rumours of that happening.

---

### Post by billenbois on 2008-07-29
I see lots of ******** in the previous posts (oh noes, i used "the" word)

First things first, right?

EAL's: 
- you very well may have *an AppArmor system* certified EAL4+ (or above)
- you very well may have *a SELinux system* certified EAL1
- you very well may have a system without neither being certified EAL1 or 4+ or any other level.

The level of insurance doesn't mean a lot. The "+" only means that you have things added from the upper level (so EAL4+ is EAL4 with some EAL5 stuff added). What's important is the protection profile and the target of evaluation. Usually this target is *VERY* narrow and usually isnt directly related to SeLinux/AA/RSBAC/GrSec/what-not.

So keep the bs out. A protection profile could very well say "this computer must function as a firewall and allow no input, and only output from tcp port xx", the target of evaluation being "iptables core with xx modules enabled". This system could run SeLinux and be certified EAL4. yet what was really tested is iptables. that's the part which is "assured" to work. That and the whole development procedure of the system.

Now, we know, that NSA and friends push SELinux *very* hard (they've been very disappointed that they couldnt push out LSM and that Smack entered as competitor).

Summary:

- SeLinux and Flask might be used everywhere in the future due to their marketing strenght unreachable by common companies.
- SeLinux is not a bad solution
- LSM is a bad solution security wise ( [http://www.grsecurity.net/lsm.php](http://www.grsecurity.net/lsm.php) [http://www.rsbac.org/documentation/why_rsbac_does_not_use_lsm](http://www.rsbac.org/documentation/why_rsbac_does_not_use_lsm)) 
- AppArmor is not a bad solution, most simple and faster than SeLinux, yet less detailled and uses paths instead of inodes (arguably, using path isn't *that* bad tho, if the system isnt broken and report accurate paths that AA expects)
- grsecurity is another good solution easy and fast, yet uses a role based model which allows things like selinux does
- rsbac is yet another good solution, which is less easy than AA and GrSec but probably more than SeLinux, yet support more functionality than any of the above

My POV:
AA is not a bad choice for a distro such a ubuntu. its easier to maintain.
SeLinux/RSBAC would be much harder to maintain with a complete policy.
Ultimately linux's namespacing and a small role based solution (like SMACK) might replace the need for complicated setups with SeLinux and the like. This is not yet ready tho.

---

### Post by Nullack on 2008-07-29
So bill are you going to be the one to pay for an apparmor system to be eal4+ certified :lolflag:

---

### Post by ajackson on 2008-07-29
> **Nullack said:**
> So bill are you going to be the one to pay for an apparmor system to be eal4+ certified :lolflag:
Erm, [SLES 10]("http://www.novell.com/products/server/application_security.html") anyone?

To post a partial quote:
> SUSE Linux Enterprise Server is certified to be compliant with the Common Criteria (CC) Controlled Access Protection Profile (CAPP) at Evaluation Assurance Level 4 with augmentations (EAL 4+)

So that discounts (with evidence) that SELinux is better than AppArmour because it has EAL4+ certification.

Oh and not only does AppArmour have EAL4+ but so does good old [Windows XP]("http://www.windowsfordevices.com/news/NS2450151940.html").

Edit: The moral of this story is not to make up wild facts without checking them first.

---

### Post by Astinus on 2008-07-29
> **Nullack said:**
> 
* EAL4+ certification would be an added feature to the marketing of Ubuntu server and further strengthen the product. This would match Red Hats certification here too.
* Ubuntu server could be additionally value added by shipping it with server roles profiles using SELinux custom tailored for typical server roles. Improve on what Red Hat supplies, to position Ubuntu ahead of Red Hat ontop of already existing things like better package management.
* Canonical can add additional profit in consulting fee's for customers who dont want to deal with the project of doing additional custom profiles for their boxes. Before people accuse me of suggesting vendor lock in, customers could choose to use another LSM, another service provider and so on.


.. and none of that matters to the vast majority of Linux users :)  A talented system administrator can lock down a box decently without needing to employ RBAC, and to an organization, time is roughly equal to money so increased administration complexity when the additional benefits cannot be justified usually results in a "Non!" ;)

I contend that the number of people who'd actually make use of the profiles is small. Most users of CentOS and Fedora (in my experience) just turn SELinux off because it's too much of a pain in the *** to them, servers which do leave it enabled often don't ever flip it to enforcing (leaving it permissive) and the *very* few servers actually using it for extra protection often just lock down things like ProFTPd and have a blanket policy allowing other code to do pretty much whatever it wants.

I've read all the books you stated, deployed many servers with all of the technologies mentioned and I maintain that SELinux is a huge pain in my left bum cheek which for 99.999995% of cases is simply not required. Tools like grSecurity and AppArmor fit the bill very nicely and don't give the administrator a migraine.

> **Nullack said:**
> Or, perhaps Canonical chooses to do nothing right now, and wait / help RSbac to be a terrific product, and go with that when its ready.

You speak with a tone suggesting you think RSBAC and grSecurity are 'new'?  Well, er, they're not and they have been around for a long time :)

I think this thread is rather reaching the end of useful discussion, as multiple people have pointed out there are profiles in Ubuntu *now* which let people use SELinux should they so choose and simply put, AppArmor is an easier and more flexible solution to providing your average end-user some extra security without them needing to undertake a degree in rocket science to make their desktops work.

/me sits back and watches people throw more popcorn on the floor. :popcorn:

---

### Post by Nullack on 2008-07-29
@ajackson

You assume to know, when a little knowledge is a dangerous thing. The "certification" that Novell got involved using non trivial changes to the default product. You also try to introduce another red herring with citing the windows "certification", which again involved a heavily customised version of MS's product.

The reason why experienced people in the field site Red Hats certification is that it does not require extensive modification to be deployed and generally useful. The MS and AppArmor certifications are not real useful certifications. In fact, the products as they come are not able to be certified. They are actually not certified.

You discounted my comment about the substantial time and money involved in EAL4+ certifications. Many Governments and companies dont want to have (a) heavily modify a product to be within spec (b) pay for their own certification.

Especially now that AppArmor does not have the financial backing of Novell, will Bill on this forum flip the money for AppArmor by default to be certified? Or who else will? You? Moreover, who's going to volunteer to write the code changes needed in AppArmor?

You have an ugly tendency to get into ad hominem approaches to your views, which like some others here not only demonstrates an unfortunate side of your character but does not help to demonstrate your views.

@PmDematagoda

Your view that the maturity of AppArmor is a reason why the number of code commits has fallen is one which ignores the status of SELinux and RSBac. How long do you think SELinux has been around and what do you think of its current maturity level? Clearly, it is reasonable to compare commits for both projects and it is clear that AppArmor isnt moving ahead with anything near the level of competing mature solutions.

Your view about how commercial companies dont want to "waste money" by using "inferior security systems" does not remain true for many significant commercial software companies. Microsoft?

@Astinis

I realise you consider Linux sufficient without MAC, RBACC and so forth but I'm yet to find any credible security professional who would agree with you. Your standards of security do not match what the industry considers to be acceptable.

There is some sectors of the economy that mandate compliance to certain security standards such as many Governments around the world and companies who provide services to Governments. The issue is not optional - its compulsory.

What I said about RSbac was that it has some interesting commits to its tree lately. In fact, some of the RSbac features have not been in RSbac for a long time as you put forth.

RSbac kinda has a kitchen sink approach and I think it will be exciting to see how this pans out when all of the features are sorted together.

---

### Post by PmDematagoda on 2008-07-29
> **Nullack said:**
> @PmDematagoda

Your view that the maturity of AppArmor is a reason why the number of code commits has fallen is one which ignores the status of SELinux and RSBac. How long do you think SELinux has been around and what do you think of its current maturity level? Clearly, it is reasonable to compare commits for both projects and it is clear that AppArmor isnt moving ahead with anything near the level of competing mature solutions.

Your view about how commercial companies dont want to "waste money" by using "inferior security systems" does not remain true for many significant commercial software companies. Microsoft?

Have you ever considered the fact that SELinux has more bugs, or more needed to be done on it? SELinux at the beginning was very hard, Fedora and Red Hat have been trying to make it simpler for everyone, but obviously it still isn't, therefore comparing commits isn't exactly the best way to compare the development of both.

Microsoft is like Novell, they remove anything that does not benefit them in anyway or if it does not hold any long-term benefits for them, if Apparmor really is as bad as you mention it then Novell would be trying to distance itself from it and stop providing it with unnecessary support, development help and advertising instead of doing the opposite.

And you failed to answer my question, how long did it take you to learn SELinux properly?

---

### Post by Nullack on 2008-07-29
The NSA's approach was kernel space development is the priority. Most of the Fedora stuff is about user space development and I was not referring to user space commits, I was on about kernel commits.

I cant comment on why Novell dropped AppArmor (Im not Novell) but I do know that there was tensions with the kernel developers about migrating it into Linus' tree on the basis of what some developers saw as technical problems.

Im not trying to be evasive about how long it took to learn SELinux. Im honestly not sure - and more to the point I think that anyone being fair to themselves would realise that learning is ongoing about Linux and its components. Honest people tend not to claim having expertise in larger projects as a whole, rather having expertise in say the networking component of the Linux kernel specifically.

Do you have any data I can look at that supports your view that SELinux has had more bugs than AppArmor?

---

### Post by Raptor45 on 2008-07-29
You have argued that SELinux is more powerful when properly configured. No one contests that.

You have argued that Red Hat has been certified with SELinux. Thats great.

You have argued that SELinux is better maintained. This has been argued, but I'll give you that point.

What you have failed to do is show how this would benefit the average end user, especially considering the time and effort which would be required to make the switch. Time and effort which could be spent elsewhere.

As previously discussed, SELinux would be difficult set up, and maintain, and is more likely to get in the user's way when not set up properly. The benefits of the better security are generally unneeded by most users, while AppArmor is, at the very least, "good enough".

---

### Post by psyke83 on 2008-07-29
> **Nullack said:**
> The NSA's approach was kernel space development is the priority. Most of the Fedora stuff is about user space development and I was not referring to user space commits, I was on about kernel commits.

I cant comment on why Novell dropped AppArmor (Im not Novell) but I do know that there was tensions with the kernel developers about migrating it into Linus' tree on the basis of what some developers saw as technical problems.

Im not trying to be evasive about how long it took to learn SELinux. Im honestly not sure - and more to the point I think that anyone being fair to themselves would realise that learning is ongoing about Linux and its components. Honest people tend not to claim having expertise in larger projects as a whole, rather having expertise in say the networking component of the Linux kernel specifically.

Do you have any data I can look at that supports your view that SELinux has had more bugs than AppArmor?

You don't even need to learn about SELinux directly. Install a recent release of Fedora and you'll encounter problems soon. It was fun trying to figure out why swfdec and Flash refused to render content in Firefox during rawhide development (answer: SELinux misconfiguration).

I get the impression that the controls are so finely-grained that you cannot get a "perfect" security profile without manually checking every application in our repositories. It's a PITA. ;)

I would say this to you, however. Don't go recommending such a serious piece of software until you've personally researched and gotten your hands dirty with it. Your opinions mean considerably less otherwise.

---

### Post by PmDematagoda on 2008-07-29
> **Nullack said:**
> Do you have any data I can look at that supports your view that SELinux has had more bugs than AppArmor?

I've had a look at the bugzilla for SELinux in SourceForge, and the Apparmor Launchpad account, however they may not be accurate/official. Perhaps someone here knows where to get the proper information required?

And psyke83, I agree with your last comment, I learned how to use Apparmor in such a way that it would sandbox Firefox and a few other applications in about an hour and therefore I came to the conclusion that Apparmor is not only pretty secure, but is also easy to use. SELinux on the other was/is much, much tougher, I have been reading manual after manual on the internet, even the official documentation yet none of them have helped me create a profile(or module as they call it on SELinux) that can properly sandbox even one process, this may be a bug, since no matter how badly I write the profile(i.e. giving it a measly number of allowances) the process still runs unconfined. I have been racking my brain about this for two days, yet I do not seem to be anywhere close to solving it.

---

### Post by Nullack on 2008-07-30
@Raptor - mate your thinking is based on Ubuntu being for Desktop linux users. I contend that Ubuntu is also making a push for servers. I do understand your argument, and I say:

* Server uses, especially Governments and Business working to Government, are often bound by mandatory standards compliance
* I think it would be possible to come up with a reasonable Desktop SELinux profile that was mostly seamless to the user. I don't discount the effort needed to be done in that however.

@psyke83 - When I said I did not have extensive experience with Fedora and Ubuntu's SELinux profile, that does not mean I do not have considerable experience with SELinux itself and other profiles :)

Im not honestly sure if running different LSM's between Server and Desktop versions would be a smart architectural choice though - I dunno about that compromise.

Maybe the Utopia to keep everyone happy will be RSbac, but thats a wait and see in my book.

---

### Post by RAOF on 2008-07-30
> **Nullack said:**
> ...
* I think it would be possible to come up with a reasonable Desktop SELinux profile that was mostly seamless to the user. I don't discount the effort needed to be done in that however.
...

I don't doubt that; Fedora has pretty much done this.  The problem is, I don't want it to be *mostly* seamless; I want it to be no more intrusive than the current AppArmour solution.

Again, SELinux makes much, much more sense for a server.  Where you really, really care about security, are running in a much more predictable environment, and can thoroughly test before deployment.

---

### Post by ajackson on 2008-07-30
> **Nullack said:**
> @ajackson

You assume to know, when a little knowledge is a dangerous thing. The "certification" that Novell got involved using non trivial changes to the default product. You also try to introduce another red herring with citing the windows "certification", which again involved a heavily customised version of MS's product.
I'm beginning to feel like a parrot. Evidence? Anything to backup these latest "facts", anything at all?

> The reason why experienced people in the field site Red Hats certification is that it does not require extensive modification to be deployed and generally useful. The MS and AppArmor certifications are not real useful certifications. In fact, the products as they come are not able to be certified. They are actually not certified.
I'm beginning to feel like a parrot. Evidence? Anything to backup these latest "facts", anything at all?

> who's going to volunteer to write the code changes needed in AppArmor?
We are back to the fallacy that no paid developers make a product rubbish.

> You have an ugly tendency to get into ad hominem approaches to your views, which like some others here not only demonstrates an unfortunate side of your character but does not help to demonstrate your views.
Cut out the personal attacks it gives a very good indication of **your** character. Also don't confuse my posts with yours when you go on about ad hominem arguments, who is the one who refuses to back up claims and starts using emotive language and personal attacks?

Also if you do decide to post in here again, post some evidence to back up your multitude of "facts". Number of commits does not equate to a good piece of development but rather (if they are bug fixes) points that a poor product is slowly being fixed. Since you rate paid developers so much what does a large number of bug fixes suggest about how good they are?

---

### Post by Nullack on 2008-07-30
@RAOF - I understand, maybe RSbac will end up developing to what your after? Your requirements are very difficult to meet in a secure context - your almost asking for some sort of AI that would decide if a user's actions are legitimate or not. Right now the solution seems to be to adopt a poorer security standard so it doesnt get in the way which any reasonable person would conclude isnt ideal. Really, there is alot of difference between "mostly" and "no more".

As stated Im not sure if there is wisdom in splitting LSMs between desktop and server products right now. I think it could be debated either way.

---

### Post by PmDematagoda on 2008-07-30
> **Nullack said:**
> @RAOF - I understand, maybe RSbac will end up developing to what your after? Your requirements are very difficult to meet in a secure context - your almost asking for some sort of AI that would decide if a user's actions are legitimate or not. Right now the solution seems to be to adopt a poorer security standard so it doesnt get in the way which any reasonable person would conclude isnt ideal. Really, there is alot of difference between "mostly" and "no more".

As stated Im not sure if there is wisdom in splitting LSMs between desktop and server products right now. I think it could be debated either way.

"Ideal" is something which can change, tell me, which is ideal:-
1) An Apparmor system that properly sandboxes the system and protects different components from each other.
or
2) An SELinux system that doesn't sandbox everything or partially sandboxes the components of the system because the profiles are too difficult to be made, like in the case of Fedora.

Seriously, if someone had the same will to create Apparmor profiles that protects the whole OS as Red Hat/Fedora has, then the Apparmor one would be further ahead than the SELinux one would be, perhaps already finished. Also, Apparmor is a lot simpler to administrate and use.

Oh, and Nullack, RAOF's expectations are typical of what a lot of desktop users actually want(even I do), they do not want to spend their time administering a security system they don't even understand if it messes up their own work/jobs, and then what happens? They turn the security system off because it becomes irksome to the people involved, and then the whole point of the security system disappears altogether. This is where Apparmor wins a bit, people only need to read a wiki for about a few minutes and they are ready to administer the system without just turning the system off and they can just unload the profile causing the problem.

---

### Post by Joeb454 on 2008-07-30
Thread closed for review

---

