---
title: "No way to dial up/Dapper leaves me stranded/LinuxSux"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by danrael on 2006-08-02
I am beginning to think all this talk about Linux is just so much fluff.  I have installed and played around with several distros, all of which have problems which really should have been addressed before being released.  I think it is a shame.  Reminds me of the Hubble telescope and the Challenger rocket:  they knew they were bad, but they launched them anyway!

You would think that Dapper is an improvement over Breezy, but is actually worse.  I was at least able to access the kppp dialer in Breezy and get online, but it is not available in Dapper.  I see it listed in "Add/Remove Applications" under the Applications menu, but when I attempt to install it, I receive a message stating:  "kpp is not available in any software channel.  The application might not support your system architecture."  My modem (which I know worked fine with Breezy) is recognized in the Device Manager, and I am able to configure my account/modem settings and activate the modem under System>Administration>Networking, but this makes no difference:  there is no kppp module available, as in Breezy and PCLinux, so I can make an internet connection.  I see the words as they are forming in my mind:  "Face it:  Linux just sux!"  Please tell me the answer is right under my nose but I just don't see it.  Thanks in advance.](*,)

---

### Post by zxee on 2006-08-02
Dapper did have big problems in networking and dial up-IMO.
Are you using kubuntu? Becuase there is no kppp in ubuntu since kppp is kde based i.e. depends on kde libraries. 
You should be able to set up an internet connection with > sudo pppconfig and then use wvdial or pon from a terminal to connect. Then you can apt-get any gui dialer that will run on your system. 
It is a shame that dapper didn't work as well in some areas, but those are the risks you face in the open source world. Windows is hardly perfect/without problems. We don't have to pay for GPL so why expect it to be at all like propritary?

---

### Post by zxee on 2006-08-02
Message auto-double posted.

---

### Post by az on 2006-08-02
> **danrael said:**
>  "Face it:  Linux just sux!"  Please tell me the answer is right under my nose but I just don't see it.  Thanks in advance.](*,)

Either your looking for the wrong thing (Kppp is not in Ubuntu, as mentioned) or you just found a bug.

---

### Post by cantormath on 2006-08-02
> **danrael said:**
>  I am beginning to think all this talk about Linux is just so much fluff. ](*,)
And you would be begining to loose your mind as well.
 
> **danrael said:**
>   I have installed and played around with several distros, all of which have problems which really should have been addressed before being released. ](*,)

Because you do not know how to use linux, you are just really good at installing now.  I suggest you stick with ubuntu and learn linux.  Linux is the kernel, all the distributions share this, so, in a sense, all you have been doing is installing different applications.

> **danrael said:**
>   I think it is a shame.  Reminds me of the Hubble telescope and the Challenger rocket:  they knew they were bad, but they launched them anyway!](*,)

How do you know anything about linux if all you have done is install a bunch of distributions.  I say, you are no astronaut   or rocket scientist.
LOL, Image how bad it would have been if Hubble ran on Windows.

> **danrael said:**
> 
You would think that Dapper is an improvement over Breezy, but is actually worse. ](*,)

actually its better.

> **danrael said:**
> 
  I was at least able to access the kppp dialer in Breezy and get online, but it is not available in Dapper. ](*,)

yes it is.

> **danrael said:**
> 
  I see it listed in "Add/Remove Applications" under the Applications menu, but when I attempt to install it, I receive a message stating:  "kpp is not available in any software channel.](*,)

I believe you, and maybe you need to change your repositories or maybe you need to change your hardware, or...........stop using dialup.

> **danrael said:**
> 
there is no kppp module available, as in Breezy and PCLinux,
 so I can make an internet connection.](*,)

yes there is kppp, and kppp viewer........and i can install it.....I just did for you.
so you "can make an internet connection"?  I know you ment can't. But you can....and its easy, even my mom can do it.
except my mom doesnt use dialup anymore.....so I guess she doesnt have to.  
Time to upgrade.  The point is pay more attention to linux.

> **danrael said:**
> 
  I see the words as they are forming in my mind:  "Face it:  Linux just sux!"
.
.
 Please tell me the answer is right under my nose but I just don't see it.  Thanks in advance.](*,)

what are you 12....!?
you are delusional and terribly wrong.  You need to buy a machine with linux installed by someone who will read the manuals.
[BUY HERE]("http://lxer.com/module/forums/t/23168/")


I bet if you let them install it, it will be able to dial into anything you need it to.  You need to more manuals and howto's and cheer up a bit before you come in here saying linux sucks*.

---

### Post by zxee on 2006-08-02
cantormath I believe it is not ubuntu's policy or code of conduct to use phrases like those you have posted to this thread. I personally find your post and tone to be offensive. 
You also do not know everything e.g there have been a lot of problems with dapper in ppp and networking.
I hope a mod sees this and can give you some advice.

---

### Post by cantormath on 2006-08-02
> **zxee said:**
> cantormath I believe it is not ubuntu's policy or code of conduct to use phrases like those you have posted to this thread. I personally find your post and tone to be offensive. 
You also do not know everything e.g there have been a lot of problems with dapper in ppp and networking.
I hope a mod sees this and can give you some advice.

I certainly dont know everything....or even most things, and I do see what you are saying about my tone.  I guess I am just responding to a similar tone hoping to get across what I was trying to say with similar language.  I certainly don't mean to be offensive; I was only expressing that the original thread was rantful and not productive.  I think a question could have been asked with out the careless insults to linux. I believe that the circumstances in which the thread was started intiated this type of conversation warrenting such a response, and thus called for.  If I had responded in a similar way to a clear neutral question, I would be ashamed and hence in agreement with your critic.

---

### Post by zxee on 2006-08-02
> **cantormath said:**
> I certainly dont know everything....or even most things, and I do see what you are saying about my tone.  I guess I am just responding to a similar tone hoping to get across what I was trying to say with similar language.  I certainly don't mean to be offensive; I was only expressing that the original thread was rantful and not productive.  I think a question could have been asked with out the careless insults to linux. I believe that the circumstances in which the thread was started intiated this type of conversation warrenting such a response, and thus called for.  If I had responded in a similar way to a clear neutral question, I would be ashamed and hence in agreement with your critic.

I do understand that we all get reactive at times-including myself.  People I think of as enlightened beings call that behavior "matching energy" so if someone displays anger often we match with it, but then that's being controlled or directed by the other person's actions. 
My primary interest in this is in the reputation and stability of this community. It's also understandable that people get frustrated with being unable to do a expected task. That doesn't reflect on ubuntu or those of us that use it. Their frustration is about them. We can however choose to respond in a helpful and even defusing way so that they might learn something and we gain from that too. Simply reacting almost assures that we will just leave the confrontation angry.
The orginal poster stated that he/she had been able to get dial up working with breezy and also specified that he/she is using the same hardware with the dapper install. So this isn't simply a case of ignorance or inability. We get a chance to defuse someone's frustration and perhaps point them at a something where they can find a solution, or we can react. 
Lots of words here-sorry-but just a reminder too that terms like read the manual-in acronym form are not allowed in the Ubuntu forums. I for one am glad of that.

---

### Post by cantormath on 2006-08-02
> **zxee said:**
> I do understand that we all get reactive at times-including myself.  People I think of as enlightened beings call that behavior "matching energy" so if someone displays anger often we match with it, but then that's being controlled or directed by the other person's actions. 
My primary interest in this is in the reputation and stability of this community. It's also understandable that people get frustrated with being unable to do a expected task. That doesn't reflect on ubuntu or those of us that use it. Their frustration is about them. We can however choose to respond in a helpful and even defusing way so that they might learn something and we gain from that too. Simply reacting almost assures that we will just leave the confrontation   angry.
The orginal poster stated that he/she had been able to get dial up working with breezy and also specified that he/she is using the same hardware with the dapper install. So this isn't simply a case of ignorance or inability. We get a chance to defuse someone's frustration and perhaps point them at a something where they can find a solution, or we can react. 
Lots of words here-sorry-but just a reminder too that terms like read the manual-in acronym form are not allowed in the Ubuntu forums. I for one am glad of that.

I agree. I took the manual comment(R#$M) out.
  I completely believe in defusing the situation in most circumstance.  No matter how mad someone gets about not getting something or the issues they have encountered, I always try to ensure them that they can do it and that its not that bad.  I always say, it is just different.  

 For instance, If a student comes to me and says "God math is sooooooo hard, it sux, I dont get it........", I will assure them, or at least try, that math is do-able, it is hard, and that it was that hard for me when I was an undergrad.  
 However, if a student, or _anyone_, says "math is pointless, I have spent lots of time with it, in its different forms and its alot of fluff. I know math sux, those guys who invented math should have never let it out there if it didnt make sense......what were they thinking......."

At that point, I think the only thing I can do, as a non-guru math user is state why they are wrong from my point of view.  I think its important that they realize they are terribly mistaken in there attack on math with vigor.  But let me tell you why.....

I occasionally hear similar points of view on linux, usually windows admins, who really havent give linux a shot, but like to think they have.  So, I attempt to challenge them a little, and get them to work a bit harder, like I did when my wireless, video card and hibernate wouldnt work.  I tell them "my non-31337 friends and family can do it, so maybe its not linux; maybe its the user".  What I do not want is someone leaving linux because they read an unanswered thread that said linux "sux", does not work and the developers were stupid to let it out; especially if the author of the thread is just a "point click engineer" on M$.  Face it, there are several "point-click engineers" who express that incorrect view to basic users, clients and children and that I think hurts the community.
Bottom line, linux users don't have to be 31337, but linux certainly is.

  Another thing, I hung out with Jeff Baily, an ubuntu developer, and the Ubuntu CFO at the Desktop Linux Summit in San Diego, as they sat there helping people, moms and dads, individually, at the lunch break, helping everyone use their computers better.  There was no question to small.  So if someone say the ubuntu folks don't know what they are doing, which suggests they aren't working hard enough, I think its important to explain why they might be wrong and challenge that opinion with spice.

again, sorry about the R$%M comment.

---

### Post by Cynical on 2006-08-03
danrael, if you truly feel that way, by all means go back to windows. Linux is for people who want to control their operating system and customize it to fit their needs. If you prefer ease of use to that then windows is the better choice at the moment.

---

### Post by danrael on 2006-08-03
I do appreciate all of the response here, but I think there is a misunderstanding of my position.  I am not angry, as in 12 year old, nor frustrated.  So let us settle that right now.  And don't give me that line of:  "If you don't like Linux why don't you go back to Windows" childish response.  You are all doing everything here but dealing with the issue I have brought to your attention.  I understand about Windows.  I understand about Linux.  That is why I am here.  Linux is saying:  "Here is a distro. It works.  Try it, you will love it"  I try it, and it does not measure up to the stated promise.  I am told I need an internet connection in order to obtain needed software, but am left with no way to get online.  Catch 22.  I am told this excuse and that excuse.  It is like buying a car, but the carburetor is shipped separately.  You are instructed to assemble it and tweak it yourself.  This is unnecessary, especially for the crucial element of getting online.  At least most of the other distros give you the carburetor along with the car.  Dapper does not make it available up front.  Free or no free, there is no excuse for this.  Don't get me wrong:  I do understand and appreciate the configurability of Linux.  But I get the feeling that what some of you are saying is:  "What do you expect for free?"  That is not the point.  If you are going to make something freely available for public use, let's make sure it's right before releasing it, and let's make sure it is user-friendly.  Why not?  My Mac fully understands this, especially so.  Why can't Linux? After all, they both are UNIX-based.  My complaint does not just apply to ppp and dial-up:  I have had a lot of problems with the cd player software and the dvd software.  They just aren't ready for prime time. Period. Sorry, but I expect something more from Linux, especially if it is advertising itself as such.  Right now, certain aspects of Linux are not right.  It jusssux.  So I am telling it like it is.  No reason to get defensive.  Just some well-deserved criticism from an impartial observer.  At least I am giving you the reason why it sux.  OK?

---

### Post by danrael on 2006-08-03
> **cantormath said:**
> 
 
How do you know anything about linux if all you have done is install a bunch of distributions.  I say, you are no astronaut   or rocket scientist.
LOL, Image how bad it would have been if Hubble ran on Windows.
[I][B]
As long as you keep using Windows as a reference, Linux will always have excuses to offer.  Once we stop looking at Windows and concentrate on how to make Linux right, it will be.  That is why Apple is so great.  Linux can be too.  But it is not, and I am telling you it is not.  The emperor has no clothes.[/B][/I]


I believe you, and maybe you need to change your repositories or maybe you need to change your hardware, or...........stop using dialup.

W***What kind of solution/attitude is that?  Why don't they dump dial-up entirely as archaic, and make DSL the entry level internet connection, at dial-up rates, like $9.95/mo?  Let's stop the fluff!***



yes there is kppp, and kppp viewer........and i can install it.....I just did for you.
so you "can make an internet connection"?  I know you ment can't. But you can....and its easy, even my mom can do it.
except my mom doesnt use dialup anymore.....so I guess she doesnt have to.  
Time to upgrade.  The point is pay more attention to linux.

***No, the point is, as I already explained, and which you have not paid attention to, that, yes, I see kppp, but I am given a message such that I am unable (yes, as in "unable") to install it.  See?  The point is, stop being so smug.***



what are you 12....!?
you are delusional and terribly wrong.  You need to buy a machine with linux installed by someone who will read the manuals.
[BUY HERE]("http://lxer.com/module/forums/t/23168/")


I bet if you let them install it, it will be able to dial into anything you need it to.  You need to more manuals and howto's and cheer up a bit before you come in here saying linux sucks*.

***No. Linux needs to be offered in such a way as to make connecting to the internet to obtain needed software immediately after install extremely easy.  Yes, easy, as in de-mystified.  The manuals should be for later, in-depth use.  But to get up and running is the point.  My Mac does this, and elegantly so.  Linux, you can do it if you try!***

---

### Post by danrael on 2006-08-03
> **zxee said:**
>  It's also understandable that people get frustrated with being unable to do a expected task. That doesn't reflect on ubuntu or those of us that use it. Their frustration is about them. 

***Not entirely.  From what I have seen, there are many instances where Linux could have been designed differently.  As it exists, the frustration factor is built in, unnecesarily so.  l think the key is for Linux engineers/programmers need to look at their product from the point of view of the user, and how the uninitiated tend to approach a task.  That is why I like Apple so much.  They seem to take the time to put themselves in the user's shoes, and it works.  Why can't Linux do this as well?  I don't think this is too much to ask, really.***

We can however choose to respond in a helpful and even defusing way so that they might learn something and we gain from that too. Simply reacting almost assures that we will just leave the confrontation angry.
The orginal poster stated that he/she had been able to get dial up working with breezy and also specified that he/she is using the same hardware with the dapper install. So this isn't simply a case of ignorance or inability. We get a chance to defuse someone's frustration and perhaps point them at a something where they can find a solution, or we can react. 

***For some reason, some of you equated my "Linux sux" comment with frustration and anger, neither of which is the case.  As far as I am concerned, if Linux were a product which was used in a life and death situation, I would toss it as defective and life endangering.  You cannot say to me:  "Well, what do you expect?  After all, it's free."  Free is not the point.  The point is that it does not work as described.  If Linux were a gun, I would be dead in a life and death situation.  It either works or it does not.  No excuses. What I am really saying here is that I see the beauty and potential of Linux, but it is not being realized, when it could be.  Not only that, but it is being offered for public use before it is ready.  That's all.  I understand there is a kind of "my OS is better than yours" attitude amongst a lot of users, which creates for defensiveness and emotional reaction, clouding the ability to see through to a solution to a problem, and getting in the way, as it obviously has here.  I wonder if someone would actually like to address the problem I have presented here.  You know, when I finally do figure this out, which I will, I will return and post a step by step procedure for the benefit of others with the same problem.***

.

---

### Post by danrael on 2006-08-03
> **zxee said:**
> Dapper did have big problems in networking and dial up-IMO.
Are you using kubuntu? Becuase there is no kppp in ubuntu since kppp is kde based i.e. depends on kde libraries. 
You should be able to set up an internet connection with  and then use wvdial or pon from a terminal to connect. Then you can apt-get any gui dialer that will run on your system. 
It is a shame that dapper didn't work as well in some areas, but those are the risks you face in the open source world. Windows is hardly perfect/without problems. We don't have to pay for GPL so why expect it to be at all like propritary?

Thank you for at least attempting a solution to my question, without the emotional reaction that others got caught up in.  At least you recognize that there is a problem with Dapper, as I have.  I will give this a try.  

I never brought up Windows in the first place, however. I was just addressing Ubuntu per se, so let us concentrate on Ubuntu, and stop looking over our shoulders.  But to answer your question:  I don't expect Linux to be at all "like proprietary", as you have suggested:  I expect it to be better.  That is why I came to Linux to begin with.  Campeche?

---

### Post by mozetti on 2006-08-03
> **danrael said:**
> ***No. Linux needs to be offered in such a way as to make connecting to the internet to obtain needed software immediately after install extremely easy.  Yes, easy, as in de-mystified.  The manuals should be for later, in-depth use.  But to get up and running is the point.  My Mac does this, and elegantly so.  Linux, you can do it if you try!***

And in 9/10 cases, it does this. Unfortunately, you seem to have stumbled upon the 1 case. Others have posted some possible solutions (before cantormath & zxee got into their 'jack) -- did you try zxee's advice? 

Here it is again:

[quote=zxee]You should be able to set up an internet connection with
```
sudo pppconfig
```[/quote]

What was the outcome?

Also, once you get it up & running (and online) you may start playing around in the CLI (command line interface). The CLI and the "man" pages aren't for [quote=danrael]later, in-depth use.[/quote] If you want your computer to be anything more than an overpriced web-tool, then using the "man" pages and CLI is essential.

I'm just starting with Linux myself (6 months or so), but I've been dabbling for a few years. My overall impression is it is a wonderful OS for people that *want* to learn. If you just want to "turn on, tune in, & drop out", you can certainly use Linux/Ubuntu to do that but it would be akin to buying a ferrari to go to the corner store. I'm assuming your the first type, since that's what get's people to Linux in the first place. So, hopefully you can get this sorted and move on with better experiences.

---

### Post by beniwtv on 2006-08-03
Personally, I think danrael has some point.

Some great software is still missing in the standard install.

Sofware that I'd like to be included:

* kppp / Gppp - or - fix the network manager tool, since it doesn't actually work with dialup

* network-manager - This is important. Ubuntu has no OOTB support for WPA/WPA2. I need this for my wifi. And don't tell me about GTKwifimanager - it doesn't work for me :(, and the applet of networkmanager is just very handy.

* bluetooth gnome file transfer program

* Graphical X config tool

Don't get me wrong. But with only these 4, we can have a lot better user experience for newbies.

I hope we will have some of them in Edgy.

---

### Post by beniwtv on 2006-08-03
* double post *

---

### Post by danrael on 2006-08-03
> **zxee said:**
> Dapper did have big problems in networking and dial up-IMO.
Are you using kubuntu? Becuase there is no kppp in ubuntu since kppp is kde based i.e. depends on kde libraries. 
You should be able to set up an internet connection with  and then use wvdial or pon from a terminal to connect. Then you can apt-get any gui dialer that will run on your system. 
It is a shame that dapper didn't work as well in some areas, but those are the risks you face in the open source world. Windows is hardly perfect/without problems. We don't have to pay for GPL so why expect it to be at all like propritary?
[I][B]
OK.  I successfully set up my parameters for dial-up with my ISP using the command you provided [sudo pppconfig] in a terminal window.  Where do I go from here, and what, specifically, are the commands I need to enter?[/B][/I]

---

### Post by danrael on 2006-08-03
> **zxee said:**
> cantormath I believe it is not ubuntu's policy or code of conduct to use phrases like those you have posted to this thread. I personally find your post and tone to be offensive. 

[I][B]
Yes.  That is definitely the problem.  You are making it personal, when it is not.  "Offensive", yes, as in:  "This product does not work properly, therefore:  "It sux" [as in: "does not work as described."] So, in order to assist you to deal with my comment, you might say something back to me like:

"Sux, eh?  OK.  Well, exactly what makes you say that?  You must have come across something really out of kilter to arrive at that conclusion."  [like, a gun that jams in a real war, perhaps, which might cause you to say:  "Hmmm...this gun sux...big time."][/B][/I]

---

### Post by cantormath on 2006-08-03
> **danrael said:**
> 

“I do appreciate all of the response here, but I think there is a misunderstanding of my position. I am not angry, as in 12 year old, nor frustrated. So let us settle that right now. And don't give me that line of: "If you don't like Linux why don't you go back to Windows" childish response.”

**You are right, he should have said go back(switch) to OSX.  Promoting windows is not going to help anyone here.  ::grin::**

“ You are all doing everything here but dealing with the issue I have brought to your attention.”

[B]You did not ask a question.  You told us what linux “is”, that the developers are stupid for launching it, and that there is no kppp module available, which there is, its just you aren't able to install it.  You also said 
"Face it: Linux just sux!" Please tell me the answer is right under my nose but I just don't see it. Thanks in advance.“
There is no question there.  It just sounds like an announcement of things you “know”,ie) that linux sux.  
[/B]
“ I understand about Windows. I understand about Linux. That is why I am here.”

**If that were true, you would not be mad at Linux.**

“ Linux is saying: "Here is a distro. It works. Try it, you will love it" I try it, and it does not measure up to the stated promise. “
[B]
That comes with a tiny assumption.  You are willing to be patient, read manuals, ask question, and most importantly learn linux.  You see, when people use Windows, or OSX they buy there computers with it alreasy installed, so.... they get to start with a perfectly working machine.  Have you ever tried taking a Copy of XP, not a recover disk, and installing it on a laptop.  50 bucks says you cannot get online 9 of 10 times, why? because the drivers for nic(or modem or mouse or videocard....)  are not included with the XP disk.  Forget using the modem, you cannot even get the modem to be recognized.  
So if you want it to be a fair comparison, you need to buy a machine with linux installed on it by someone who knows what they are doing, someone who has learned linux, or.....install it right and then compare.  

Note, I gave a link to where you could buy such a machine from about 50 different companies...
[http://lxer.com/module/forums/t/23168/](http://lxer.com/module/forums/t/23168/)
my favorite is 
[http://lxer.com/module/forums/t/23168/](http://lxer.com/module/forums/t/23168/) [/B]

“ I am told I need an internet connection in order to obtain needed software, but am left with no way to get online. Catch 22. I am told this excuse and that excuse. It is like buying a car, but the carburetor is shipped separately.  You are instructed to assemble it and tweak it yourself. This is unnecessary, especially for the crucial element of getting online. At least most of the other distros give you the carburetor along with the car. Dapper does not make it available up front. Free or no free, there is no excuse for this. “

**same as response above.  Try it with XP on a laptop.**

“Don't get me wrong: I do understand and appreciate the configurability of Linux.”

**No, you said linux sux.**

“ But I get the feeling that what some of you are saying is: "What do you expect for free?" 
That is not the point. If you are going to make something freely available for public use, let's make sure it's right before releasing it, and let's make sure it is user-friendly. Why not? “
[B]
It is right, and user friendly, and only getting better.
 Not only is linux free, Its better.  But installation, regardless of the os, take a little understanding of what you are installing.  Again, try installing XP on a latop with just the XP disk.
[/B]
“Why can't Linux? After all, they both are UNIX-based. My complaint does not just apply to ppp and dial-up: I have had a lot of problems with the cd player software and the dvd software. “

[B]People have the same problems on other os's, the diffence is, you learned the software, and they have not.  I have clients that still call me once a month asking if I will come by and show them how to burn a cd.  If you have problems, you need to ask specific questions, and learn linux.  If you do not want to deal with it, you can go to [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid) and get Desktop support from Canonical support services.  
[/B]
“They just aren't ready for prime time.  Period. Sorry, but I expect something more from Linux, especially if it is advertising itself as such. “

[B]They are prime time:
Linux in Business (prime time?)
[http://mtechit.com/linux-biz/](http://mtechit.com/linux-biz/) 
IMS Research
[http://www.commsdesign.com/news/insights/showArticle.jhtml?articleID=191600051](http://www.commsdesign.com/news/insights/showArticle.jhtml?articleID=191600051) 
Business model
[http://www.csclub.uwaterloo.ca/media/Software%20development%20gets%20on%20the%20Cluetrain.html](http://www.csclub.uwaterloo.ca/media/Software%20development%20gets%20on%20the%20Cluetrain.html) 
Redhat vs. Ubuntu
[http://www.freesoftwaremagazine.com/articles/editorial_13](http://www.freesoftwaremagazine.com/articles/editorial_13)
China: The Republic of Linux (the country)
[http://www.g4tv.com/screensavers/features/39528/China_The_Republic_of_Linux.html](http://www.g4tv.com/screensavers/features/39528/China_The_Republic_of_Linux.html) 

[/B]“Right now, certain aspects of Linux are not right.”

**Got to to learn it and use it on a proper install to say that.**

“ It jusssux. So I am telling it like it is. No reason to get defensive. Just some well-deserved criticism from an impartial observer. At least I am giving you the reason why it sux. OK?”

[B]But I thought you had a question?
[/B]
“As long as you keep using Windows as a reference, Linux will always have excuses to offer. Once we stop looking at Windows and concentrate on how to make Linux right, it will be. That is why Apple is so great. Linux can be too. But it is not, and I am telling you it is not. The emperor has no clothes.”

[B]You didn't answer the question, how do you know anything about linux if all you have done is install a bunch of distributions.  For you to help “fix” linux, we the community, need your help, learn linux, install it properly, or buy a box with a preinstall, and contribute the community invites you.
[/B]
“Why don't they dump dial-up entirely as archaic, and make DSL the entry level internet connection, at dial-up rates, like $9.95/mo? “

[B]Because broadband is better, ie) cox or charter. ::grin:: 
[/B]
“No, the point is, as I already explained, and which you have not paid attention to, that, yes, I see kppp, but I am given a message such that I am unable (yes, as in "unable") to install it. See? The point is, stop being so smug.”

[B]If all you had said was the problem and that you pissed about it, some of the community might have quickly helped you through it or help you find an alternative, but you didnt do that. 
[/B]  
“ No. Linux needs to be offered in such a way as to make connecting to the internet to obtain needed software immediately after install extremely easy. Yes, easy, as in de-mystified. The manuals should be for later, in-depth use. “

[B]That would be like trying to drive before you learn to drive.  

[/B]“ But to get up and running is the point. My Mac does this, and elegantly so. Linux, you can do it if you try! “

[B]If you BUY a recovery, Im sure that is true about all mac or pc/laptops using OSX or windows.
But I guarentee if you take any PC and try to put OSX for PC hardware on it, it will not be elegant. But with ubuntu, or suse, or redhat, you can take just about any desktop, and most laptops, and have everything working with little or no setup.  I have never had an issue with ubuntu and a desktop pc.

[/B]“ From what I have seen, there are many instances where Linux could have been designed differently.”

[B]What! you have only installed a bunch of distro's, improperly I might add; how does that qualify anyone to discuss the design flaws in linux.

[/B]“ As it exists, the frustration factor is built in, unnecesarily so. l think the key is for Linux engineers/programmers need to look at their product from the point of view of the user, and how the uninitiated tend to approach a task. That is why I like Apple so much. They seem to take the time to put themselves in the user's shoes, and it works. Why can't Linux do this as well? I don't think this is too much to ask, really.”

[B]We can however choose to respond in a helpful and even defusing way so that they might learn something and we gain from that too. Simply reacting almost assures that we will just leave the confrontation angry.
The orginal poster stated that he/she had been able to get dial up working with breezy and also specified that he/she is using the same hardware with the dapper install. So this isn't simply a case of ignorance or inability. We get a chance to defuse someone's frustration and perhaps point them at a something where they can find a solution, or we can react. 
[/B]
“ For some reason, some of you equated my "Linux sux" comment with frustration and anger, neither of which is the case. As far as I am concerned, if Linux were a product which was used in a life and death situation, I would toss it as defective and life endangering.”

[B]The US Navy disagrees 
[http://news.zdnet.co.uk/software/linuxunix/0,39020390,39280200,00.htm](http://news.zdnet.co.uk/software/linuxunix/0,39020390,39280200,00.htm)
[/B]

“ You cannot say to me: "Well, what do you expect? After all, it's free." Free is not the point. The point is that it does not work as described. If Linux were a gun, I would be dead in a life and death situation. It either works or it does not. No excuses.”

[B]That is like say, Since I cannot fly this plane, the plane must be broken.  I would pay for linux if it were not free.  If linux was a gun!?  If linux was a gun, it would be a nuclear weapon, and windows a granade.
[/B]
“ What I am really saying here is that I see the beauty and potential of Linux, but it is not being realized, when it could be.”

[B]Again, refer to the Links above and the US Navy.
[/B]
“ Not only that, but it is being offered for public use before it is ready. “

[B]The car runs just fine, you just have a licence yet, but we want you learn ::grin::
[/B]
“ I wonder if someone would actually like to address the problem I have presented here.”

[B]ask the question, be ready to answer questions, and stop thinking you understand linux, because you clearly don't.
[/B]
“ You know, when I finally do figure this out, which I will, I will return and post a step by step procedure for the benefit of others with the same problem..”

[B]Thats the idea.
[/B]


You need to learn linux.  Start with this..
[http://www.oreilly.com/catalog/ubuntuhks/](http://www.oreilly.com/catalog/ubuntuhks/)
I will send you a copy if you dont want to buy it.

---

### Post by zxee on 2006-08-03
> **danrael said:**
> [I][B]
OK.  I successfully set up my parameters for dial-up with my ISP using the command you provided [sudo pppconfig] in a terminal window.  Where do I go from here, and what, specifically, are the commands I need to enter?[/B][/I]

I think I included, in my orginal reply, that you can use pon from the command line to connect to your isp. e.g. > pon <name of provider or account created with pppconfig>

If you're still with us let the thread know how that works for you. It may help others too.

---

### Post by danrael on 2006-08-03
Thanks for your response.  I will try this and keep you posted as to the results.

---

### Post by danrael on 2006-08-03
[B]"You did not ask a question. You told us what linux “is”, that the developers are stupid for launching it, and that there is no kppp module available, which there is, its just you aren't able to install it. You also said
"Face it: Linux just sux!" Please tell me the answer is right under my nose but I just don't see it. Thanks in advance.“
There is no question there. It just sounds like an announcement of things you “know”,ie) that linux sux."[/B] 

*[COLOR="Blue"]I did not say the developers are stupid; you did.  I implied that they were not thinking things through enough.[/COLOR]*

[I][COLOR="Blue"]I did not say that kppp is not there at all; I said that it is not available [for install], as I recieved the message after clicking the "add/remove" button:  "kpp is not available in any software channel."  That is what Ubuntu said, not I.  True, I was not able to install it, hence the reason for my coming to this forum in the first place, AFTER I tried consulting some of the resident docs, to no avail.

Everyone understands that a flashing cursor is prompting the user to respond.  I said:  "Please tell me the answer is right under my nose but I just don't see it."  Others here did understand correctly that this WAS my question, but you were focused on something else.[/COLOR][/I]  

**"If that were true, you would not be mad at Linux."**

*[COLOR="Blue"]I am not 'mad at Linux':  that is just your take on my comments.  You think I am mad because YOU are responding emotionally.  To say "Linux sux" does not necessarily imply anger.[/COLOR]*

**"That would be like trying to drive before you learn to drive."**

*[COLOR="Blue"]I pretty much know how to drive.  That is not the problem.  It's just that the car they delivered has no steering wheel installed,  the installation of which is not readily apparent or available. The owner's manual says the steering wheel can be found in the trunk.  I open the trunk, and a note says that no steering wheel is available for installation, and that I must drive the car to the dealer in order to obtain the steering wheel.  The car has the potential for being a great car, moreso than other cars which are speeding by, but right now, this particular car sux.  When I asked a passerby about the car, he only responded: "What do you expect for free?"  If you don't like it, why don't you just buy a car, or go back to the crappy car you used to own, or, better yet, why don't you just learn to drive!"[/COLOR]*  

**"What! you have only installed a bunch of distro's, improperly I might add; how does that qualify anyone to discuss the design flaws in linux."**

*[COLOR="Blue"]No, you are wrong, sir.  I did not 'just install a bunch of distros'.  If they were improperly installed, then it was not myself who did this:  the install was executed by the OS itself, pretty smoothly, I might add.  I have no complaint with that.  After the installations, I made every effort to understand the lay of the land, following every clue to make things work.  What qualifies me, AS A USER, NOT AN EXPERT, to discuss design flaws, is that I see HOW it is laid out, and it can be laid out and presented in a much better way.  As an example:  Japanese auto workers were studied to see how they completed a particular task.  If a task required, say, 20 different moves, by placing materials and tools in more strategic locations, and altering the sequence, the moves might be cut down to, say, 12 moves to complete the same task.  No additional machinery or expense is required, which would have been the western approach to solving the problem.  This seems to be what Apple has done with their OS.  One is not immediately aware of this.  It is in actual use that one appreciates all the little touches of Mac OS X which add up to elegance and ease of use, and use is the bottom line for any OS.  Please don't childishly write back and tell me that if I don't like Linux to go back to Mac OS X or Windows.  I like Linux, but it still sux.  It needs to go back to the drawing board, and get more polish.  Faster, pussycat, faster![/COLOR]*
[-(

---

### Post by danrael on 2006-08-03
> **zxee said:**
> I think I included, in my orginal reply, that you can use pon from the command line to connect to your isp. e.g. 

If you're still with us let the thread know how that works for you. It may help others too.

_________________________________________

[COLOR="Blue"]OK.  Here is where I am at:

After succesfully configuring my ISP with: sudo pppconfig, as you suggested, I open a terminal window, and type:

   pon copper

('copper' being the name of my ISP, which I used instead of
'provider', which was suggested by the pppconfig utility.)

I press 'Enter', but nothing happens, except for another prompt, consisting of:  user@ubuntu:~$

_________________________________

These are the files in my etc/ppp/peers folder:

copper
copper.bak
ppp0
provider.bak
wvdial
wvdial-pipe[/COLOR]

:-\"

---

### Post by danrael on 2006-08-03
[COLOR="Blue"]I think it is wonderful that the US Navy, governments, and large corporations are gravitating to Linux.  They have the money and the staff to make Linux work from an expert point of view.  Most of us are not experts, and we lack the money to pour down the Microsoft drain, only to get compromised performance in return.  That is partly why we come to Linux.  All I am saying is that, for the average user who is also willing to consult the docs to a reasonable level without having to become an expert,  to connect the dots from installation to full operation needs to be a smoother procedure.  From what I have seen, there are some areas where the developers did not consider this from a user point of view.  Sure, it is a piece of cake for them.  As a user, I am also in the best position to be the inspector for quality control.  I see a problem, and I return the product to the point of origin with the instruction:  "fix this:  it is incorrect or insufficient."  This is true for reporting bugs.  Why can't it also be true for design flaws?[/COLOR]

---

### Post by w_r_cromwell on 2006-08-03
Well ya know....

I'm a country boy and a real hick. To me 'sux' is a vulgar epithet. There are probably other real hicks here, too. I did manage to look past the 'fighting words' you spewed and would have responded but somebody else already gave you your solution. Note...there is always more than one wy to do things.

If some of us dump dialup we will be back to strings and tin cans or smoke signals. Yes, Virginia... there really are places where dialup is all that is available. Now everybody lighten up and lets move on.

Bill

---

### Post by danrael on 2006-08-03
> **w_r_cromwell said:**
> Well ya know....

I'm a country boy and a real hick. To me 'sux' is a vulgar epithet. There are probably other real hicks here, too. I did manage to look past the 'fighting words' you spewed and would have responded but somebody else already gave you your solution. Note...there is always more than one wy to do things.

If some of us dump dialup we will be back to strings and tin cans or smoke signals. Yes, Virginia... there really are places where dialup is all that is available. Now everybody lighten up and lets move on.

Bill
[I][COLOR="Blue"]
It's all because of the way you look at it.  Think of the word "sux" as an affectionate, humorous term, so the next time someone says to you:  "Hick, you suck", you will just laugh and end up having a beer with him, instead of you, him, or both of you ending up in the hospital, and starting a blood feud between your two families which will go on for generations.  And it will all be because you are smarter than that, and can demonstrate that hicks have real savvy and always know how to act.  People will say:  "Hey, isn't that the Cromwell boy?  He is SO intelligent and handsome!"  Heaven forbid that you would die fighting in defense of some silly Operating System called Linux. If you use Linux, and someone said:  "Your OS sux.", you might respond with:  "Ya know, you're right.  There are a couple of problems with it I noticed too.........".  Who knows?  We might even be so lucky that others will also refer to our country in such terms, allowing us to correct problems which we might not otherwise know about.  

When I suggested that dial-up be dumped, I did not mean by its users:  I meant it should be relegated to the Museum of Ancient and Archaic ISP's, and the next best system, which I believe is DSL, can take its place for general entry level use amongst the general populace, at the same price we are now paying for dial-up.  To me, that is being progressive.

The conceptual IDEA of Linux is a progressive idea as well, but the actual product as developed has some glaring flaws which, to me, are inexcuseable.  This seems to permeate Linux from distro to distro, all in different ways and degrees.  The keywords here are Quality Control and User Friendly, both of which now need to be addressed and refined to a degree which incorporates all of the wonderful features of Linux along with the wonderful features of Mac OS X and even some features of Windows.  Yes, we need capitalism, but socialism and communism have some features which can be incorporated into a wholistic, functioning system that works better than just capitalism by itself.  

I get the idea that Linux is released to the general public which acts as a guinea pig for testing.  This phase should have been completed before release by proper testing and evaluation.  [/COLOR][/I]

[I]signed,

a fellow Hick  (yuk, yuk)[/I]:lol:

---

### Post by MarkSheely on 2006-08-03
Why are we even having this debate on this thread?  Future Ubuntu users who need help getting their dial-up configured are not going to be helped by any of this - I suspect it will put them off a great deal.  

There are better subcategories in the forum for this discussion, in my opinion.

--Mark

---

### Post by danrael on 2006-08-04
> **MarkSheely said:**
> Why are we even having this debate on this thread?  Future Ubuntu users who need help getting their dial-up configured are not going to be helped by any of this - I suspect it will put them off a great deal.  

There are better subcategories in the forum for this discussion, in my opinion.

--Mark
[I][COLOR="Blue"][B]
Your point is well-taken.  Rather than get side-tracked on the pitfalls and features of the Linux OS, we should be addressing the issue at hand, namely, how to establish a dial-up configuration and connection in Dapper, which, unlike its predecessor, Breezy, gives one less of a clue as to how to achieve that goal, which was my original issue.  So far, it appears that one must somehow know ahead of time that there exists a little utility called pppconfig, which will allow one to establish a connection, as kppp, which, though present, is not available for installation.  At least that is the message Ubuntu is giving me, hence, my post.  At any rate, if someone would be so kind as to pick up where I left off a few posts back, perhaps we can all benefit here.  I will be glad to be the guinea pig and do all the testing until we arrive at success, whereupon I will be more than happy to submit a detailed synopsis of the prodedure.  How does that sound?[/B][/COLOR][/I]

---

### Post by zxee on 2006-08-04
>  Originally Posted by MarkSheely  View Post
Why are we even having this debate on this thread? Future Ubuntu users who need help getting their dial-up configured are not going to be helped by any of this - I suspect it will put them off a great deal.

There are better subcategories in the forum for this discussion, in my opinion.

--Mark
> I will be glad to be the guinea pig and do all the testing until we arrive at success, whereupon I will be more than happy to submit a detailed synopsis of the prodedure. How does that sound?
Reply With Quote

This whole thing/thread IMO points up one of the flaws with the forums.Which is not being able to easily locate an answer to a problem. 
The information is on this site but it's such a big site that some of us end up chasing our tails.
Because I use dial up I often try to help people with these problems. I have some years of experiance with debian too, and debian and therfore ubuntu has some quirks in ppp. 
Again that's my opinion comparing to distros like slackware. However there is also the delayed release of dapper situation which was suppose to assure that it, dapper, not be released too buggy. At least that's how I understand it. 

In my experiance breezy and even hoary were not too difficult to set up dial up in. In my experiance dapper was terrible, and that's from perspective of someone (myself) with over six years of linux dabbling. I did file a bug report about gnome-ppp and network tools but it was rejected. I probably didn't do a good enough job defining the problem. BTW I'm using edgy now and ppp/dial up sets up very easily.

Danrael, I most often try to be helpful and consider what's it's like to be the person having the problem because I've been there. I'm glad to hear that you're willing to help with this problem-the forums can use all the help we can get. However it would be dishonest of me to say that you have treated the people here with equal regard. Your posts are defensive of your point of view and occasionally caustic. I hope you do stay and help us grow  as a community. If you do you will see that to solve problems requires the co-operation of the person with the problem.

There are places here to air grievences and opinions-as was previously brought up these help forums are not the place for that.
I've gone on too long already. 
I did locate an official how to for dial modem users here: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
and within that is a "Dapper 6.06 Special Instructions" section. 
I will put a link to that in my sig.

---

### Post by danrael on 2006-08-05
> **zxee said:**
>  


Danrael,....  it would be dishonest of me to say that you have treated the people here with equal regard. Your posts are defensive of your point of view and occasionally caustic. I hope you do stay and help us grow  as a community. If you do you will see that to solve problems requires the co-operation of the person with the problem.



*[COLOR="Blue"]**Thank you for your response.  I think if you go back and re-read the entire thread, you will see that it was not I who made the first attack on anyone personally at all.  I presented my problem specifically, and included a negative comment regarding the operating system.  Big deal.  Any mature person would have sense enough to overlook that comment and address the issue at hand.  Instead, precious energy was wasted in discussing side issues. After that, if you read on, you will see that several people on this forum are the ones who mounted personal attacks on me, even resorting to name-calling (eg:  "delusional", "12 year old", etc.) and treated me in a way which was equal to "If you don't like it here, why don't you just leave" in attitude.  One poster even suggested that my comment about the Linux OS translated to "fighting words", taking a confrontational stance.  I went back over and glanced over the entire thread, re-reading the important points, and quite frankly, I am confused by your response here, that I have treated others on this forum with disrespect.  On the contrary, I have done everything possible to attempt to steer attention back to the issue at hand, apparently to no avail.  Some of the comments made were patently false, and I have tried to correct these statements, which you are calling defensive.  I really don't get what you are trying to say to me, as I have attacked no one here.  On the contrary, it seems to me that you are all out of joint simply because I made a negative comment about the operating system which you are using, and it is perhaps all of you who have reacted defensively, unnecessarily so.  I have tried to explain that my comment is the result of exposure to several Linux distros, and what I see (or do not see) going on with them, culminating in a tentative conclusion that they contain serious flaws which are, in my opinion, inexcuseable.  I further explained that my comment had no anger or frustration, as some of you seemed to think, behind it.  One person even interpreted it as a "vulgar epithet", which only has to do with his own cultural indoctrination.  My meaning had absolutely nothing to do with what he had in mind.  Are you saying that my comment implied disrespect for the others on this forum, disrespect which I feel they actually have shown to me?  Or that I ever attacked anyone on a personal level, or resorted to name-calling, as they have?  I welcome you to please, sir, show me exactly where you feel I have shown any disrespect in any way toward anyone on this forum.  And, if you cannot, I am requesting that you withdraw what amounts to an accusation and false information.  Thank you very much.**[/COLOR]*

---

### Post by unisol on 2006-08-05
does dapper support your modem if not and you have a winmodem you may have to download drivers for it. try wvdialconf/etc/wvdial.conf and see if dapper detects your modem if it does then go to system/adminstration/networking and fill in the info ti activate ppp or you can rclick add to panel and add the dialup applet to the taskbar and fill in info  your isp phone # username and password etc

---

### Post by Cariboo1938 on 2006-08-05
Hello danrael,
I'm not sure if you have your dial-up connection already running. I struggled for about 2 days with the same problem, and now finally I'm connected.
What did I do? I have a hardware modem and I followed all the instructions given here:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
Every step worked as described. Try it---It works...Ubuntu is great!:-({|=

---

### Post by danrael on 2006-08-06
> **unisol said:**
> does dapper support your modem if not and you have a winmodem you may have to download drivers for it. try wvdialconf/etc/wvdial.conf and see if dapper detects your modem if it does then go to system/adminstration/networking and fill in the info ti activate ppp or you can rclick add to panel and add the dialup applet to the taskbar and fill in info  your isp phone # username and password etc

*[COLOR="Blue"]Yes, Dapper has detected my internal hardware modem and sees it on /dev/ttyS4.  However, in entering the modem parameters under Network Settings, it does not allow for any port beyond /dev/ttyS3.  If nothing is entered in the open field for port info, the modem connection cannot be activated, as the radio buttons remain grayed out.[/COLOR]*

---

### Post by unisol on 2006-08-06
select ttys3 backspace over 3 and enter 4 my other modem was configured at ttys14 and it worked just fine

---

### Post by Twinsen on 2006-08-06
How do u delete messages lol

---

### Post by Cariboo1938 on 2006-08-06
> **danrael said:**
> *[COLOR="Blue"]Yes, Dapper has detected my internal hardware modem and sees it on /dev/ttyS4.  However, in entering the modem parameters under Network Settings, it does not allow for any port beyond /dev/ttyS3.  If nothing is entered in the open field for port info, the modem connection cannot be activated, as the radio buttons remain grayed out.[/COLOR]*
You have to change it in the pppconf dialog. Mine is also recognized as ttyS4 and it works perfect.

---

### Post by danrael on 2006-08-08
> **Cariboo1938 said:**
> You have to change it in the pppconf dialog. Mine is also recognized as ttyS4 and it works perfect.

*[COLOR="Blue"]Yes, I understand.  As I did explain, the modem was detected as actually residing on ttyS4, so I opened up pppconfig and simply changed the parameter from ttyS1 to ttyS4.  That took care of that.  What I am talking about is configuring the modem port in the kppp dialer app itself, where the port choices only go up to ttyS3, and cannot be altered.  If you leave the field blank, you cannot proceed with connection.  So what to do?[/COLOR]*

---

### Post by mercurysquad on 2006-08-08
If you have configured your ISP details, just run wvdial <ISPname>
If that doesn't work, try sudo wvdial <ISPName>.
You should leave it running, i.e. don't close it otherwise you will get disconnected.

If it still doesn't work, post your ISP info and I will tell you how to change the wvdial.conf file properly. I had some problems as well because I use not a regular modem but one built into a mobile phone. But wvdial works great... took about 2 searches to figure it out.

Try not to use graphical PPP programs by the way.. sometimes they assume they are too intelligent, i.e. idiot-proof. (hehe.. I had to set Stupid Mode = 1 in wvdial.conf for it to work properly with my phone..)

---

### Post by mercurysquad on 2006-08-08
By the way, run ** sudo wvdialconf ** and it will auto-detect your modem and set it as /dev/modem ... make sure your modem is turned on and plugged in.

Then in kPPP you may be able to choose /dev/modem instead of ttyS4.
It's a guess. I don't use kppp.

---

### Post by danrael on 2006-09-02
> **danrael said:**
> *[COLOR="Blue"]Yes, I understand.  As I did explain, the modem was detected as actually residing on ttyS4, so I opened up pppconfig and simply changed the parameter from ttyS1 to ttyS4.  That took care of that.  What I am talking about is configuring the modem port in the kppp dialer app itself, where the port choices only go up to ttyS3, and cannot be altered.  If you leave the field blank, you cannot proceed with connection.  So what to do?[/COLOR]*

***Found the fix for this:  In the Kppp dialer, choose ttyS3, delete the '3', and enter a '4' in its place.  The port choices do not appear to be editable, but they are.  This will fix the port choice in Kppp, allowing you to now enter your username and password on the first window, previously greyed out.  Remember, you must also manually enter ttyS4 into the pppconfig utility when prompted.***  =D>

---

### Post by Ptero-4 on 2006-09-24
Another trick. if you use pon you can use plog to see what's going on. An error about not being able to get terminal parameters means your modem wasn't detected properly, lines with ALARM or failed means something stopped the connect sequence (usually a busy line, wrong username/password or the ISP server dropped the conection (which some ISP's do when they detect that you're using linux or mac instead of windoze).), the "got it/ send" (or something similar) message means that the conection was initiated and when you see a bunch of IP adresses you're online.

Ahh. one more thing. Dapper have issues recognizing modems that use non-standard ports and/or irqs.

---

