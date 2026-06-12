---
title: "AppCenter"
date: 2009-05-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jsmidt on 2009-05-26
According to a comment on this [blog]("http://californiaquantum.wordpress.com/2009/05/26/ubuntu-i-hope-appstore-rumor-true/"), PackageKit was discussed today at UDS but was shot down in favor of gnome-app-install as the base for the new [AppCenter]("https://wiki.ubuntu.com/AppCenter").

---

### Post by ghindo on 2009-05-26
If this is really the case (I'd like to see some confirmation on this), then it just seems like a poor decision on Canonical's part.  Why throw development effort into AppCenter when other projects can be utilized?

---

### Post by taavikko on 2009-05-26
> **ghindo said:**
> .
.
poor decision on Canonical's part.  Why throw development effort into AppCenter when other projects can be utilized?

+1

packagekit could be harnessed to fill users needs.
Wasting time and effort to pursue invention of a wheel, seems ridiculous.

---

### Post by Reiger on 2009-05-26
So let me get this straight (after reading the concept page): 

If you are correct, Canonical will *not* incorporate a ready-made "package management for dummies and the more experienced alike" (which is how PackageKit manifests itself to the end user) in favour of a new completely-vapor-ware-at-this-point "package management for dummies and the more experienced alike" ...?

---

### Post by 23meg on 2009-05-26
AppCenter will "utilize other projects" in any case. It's just that the consensus *in the session* wasn't exactly towards utilizing PackageKit *at this time*. It can change, before things really take off during the Karmic cycle, or at some future point through backend-agnostic design.

It's also important to note that there wasn't a thorough discussion of which backend to use during the session. Other issues such as the presentation of package descriptions and how to make it easy for developers to ship packages through the environment took most of the time.

---

### Post by mpt on 2009-05-26
I led the AppCenter session, and I was the one who posted the comment jsmidt is quoting. 23meg is correct in that there wasn’t a detailed discussion of back ends. (We had only two hours, and many topics to cover in this first overview.) I would not be at all surprised if we adopted parts of PackageKit at some stage, *e.g.* for codec and font installation.

> **ghindo said:**
> Why throw development effort into AppCenter when other projects can be utilized?

That’s a bizarre statement. :) I could just as well say: Why throw development effort into PackageKit when other projects can be used?

---

### Post by psyke83 on 2009-05-26
> **mpt said:**
> That&#8217;s a bizarre statement. :) I could just as well say: Why throw development effort into PackageKit when other projects can be used?

Because PackageKit already exists beyond a concept phase? Because Fedora (and most likely, other distributions) seem to be moving towards adoption in the same way as PulseAudio was? Because contributing to a cross-distribution project (instead of a project intended only for a single distribution) will increase good-will between ourselves and upstream, as well as other distributions? I don't consider it such a bizarre statement... ;)

I hear that you haven't decided on a backend, but it really seems like a good idea to consider PackageKit. If you "modularize" AppCenter so that it can use a vanilla PackageKit backend (or at least introduce changes that upstream would like to use themselves), then you can maintain full control over the development process, rather than find yourself limited by upstream.

---

### Post by yoasif on 2009-05-26
even if it's not based on packagekit, the appcenter sounds really good, and can only help in uptake -- anything that makes installing apps easier will be great (for newbies and end users).

---

### Post by taavikko on 2009-05-26
> **yoasif said:**
> even if it's not based on packagekit, the appcenter sounds really good, and can only help in uptake -- anything that makes installing apps easier will be great (for newbies and end users).

anything improving this "mess" (not per se) on current status is welcomed.
add/remove | synaptic | software-sources ->> Single utility :)

I'll wait anxiously for what future brings to this blueprint.

---

### Post by whoop on 2009-05-26
I'm probably the only one, but I find Ubuntu getting increasingly more "commercial". I have the feeling that this AppCenter is (at least partially) a money making scheme (soon it'll be an AppStore).
Not that I have problems with people trying to make money, but, not in the face :(

---

### Post by xebian on 2009-05-26
> **psyke83 said:**
> ....
I hear that you haven't decided on a backend, but it really seems like a good idea to consider PackageKit. ...

PackageKit is a front end. When you talk about backend, you are talking APT which is the core of Debian based installation.  Unless Ubuntu moves to RPM.  That would be bizzare. IMHO.

KDE already has kpackagekit which is a frontend to packagekit

---

### Post by Taiebot65 on 2009-05-26
I have got exactly the same feeling...It s turning like the applestore Everybody is doing that even java. But it's certainly not the right way to go. I do prefer be a friends of gnome  and promote free software and make those applications available to everyone


We will see...

---

### Post by taavikko on 2009-05-26
> **xebian said:**
> PackageKit is a front end. When you talk about backend, you are talking APT which is the core of Debian based installation.  Unless Ubuntu moves to RPM.  That would be bizzare. IMHO.

Actually "apt" is frontend to "dpkg" likewise pkgkit can be utilized to be frontend for it.

---

### Post by Gourgi on 2009-05-26
looking forward to see the AppCenter in karmic 

> **mpt said:**
> I would not be at all surprised if we adopted parts of PackageKit at some stage, *e.g.* for codec and font installation.
i hope this automatic  install is included too :D

---

### Post by davideotape on 2009-05-26
> **yoasif said:**
> even if it's not based on packagekit, the appcenter sounds really good, and can only help in uptake -- anything that makes installing apps easier will be great (for newbies and end users).

+1

I don't get why people are so critical of everything. The devs are doing everything they can to give us yet another great release, but there are people on the forums complaining. I'm all for constuctive criticism, but people complaining that this new system will be commercialized when none of the devs have even mentioned or hinted at this seems to me to be too far. Though I'm not at uds, I've been tuning into the live audio, hanging out on irc and using gobby to see what's going on. IMHO, everyone at uds is doing a great job in trying to make Karmic a great release, and I wish them every success in doing so :D

---

### Post by cszikszoy on 2009-05-26
Have any of you really used packagekit?  I know it sounds great on paper, but believe me, ubuntu's "Add/Remove" is light years ahead in terms of usability and understandability.  Packagekit may very well be the way to go, but I'm glad the decision was made to hold off for now.

---

### Post by binbash on 2009-05-26
> **whoop said:**
> I'm probably the only one, but I find Ubuntu getting increasingly more "commercial". I have the feeling that this AppCenter is (at least partially) a money making scheme (soon it'll be an AppStore).
Not that I have problems with people trying to make money, but, not in the face :(

Second that.

---

### Post by davideotape on 2009-05-26
> **whoop said:**
> I'm probably the only one, but I find Ubuntu getting increasingly more "commercial". I have the feeling that this AppCenter is (at least partially) a money making scheme (soon it'll be an AppStore).
Not that I have problems with people trying to make money, but, not in the face :(

Just out of interest, where have you seen ubuntu getting commercial? I can't really think of any ways it's being commercialized off the top of my head...

---

### Post by binbash on 2009-05-26
> **davideotape said:**
> Just out of interest, where have you seen ubuntu getting commercial? I can't really think of any ways it's being commercialized off the top of my head...

Ubuntu One...

[https://ubuntuone.com/plans/](https://ubuntuone.com/plans/)

$10.00 (USD) per month >> This is what makes the project commercial ;)

---

### Post by davideotape on 2009-05-26
> **whoop said:**
> I'm probably the only one, but I find Ubuntu getting increasingly more "commercial". I have the feeling that this AppCenter is (at least partially) a money making scheme (soon it'll be an AppStore).
Not that I have problems with people trying to make money, but, not in the face :(

> **binbash said:**
> Ubuntu One...

[https://ubuntuone.com/plans/](https://ubuntuone.com/plans/)

$10.00 (USD) per month >> This is what makes the project commercial ;)

But there's a free option. And they're not marketing it in our faces. It's offering a service, that they couldn't really offer for free otherwise.

---

### Post by whoop on 2009-05-26
> **binbash said:**
> Ubuntu One...

[https://ubuntuone.com/plans/](https://ubuntuone.com/plans/)

$10.00 (USD) per month >> This is what makes the project commercial ;)

Landscape [http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape), a really useful technology, closed source and not free (as in money) 

I **am** glad that there are discussions about open sourcing launchpad :D

---

### Post by whoop on 2009-05-26
> **davideotape said:**
> But there's a free option. And they're not marketing it in our faces. It's offering a service, that they couldn't really offer for free otherwise.

Mark Shuttleworth is talking about making Ubuntu One a default part of the Ubuntu desktop experience if I am not mistaken.

---

### Post by jsmidt on 2009-05-26
> **binbash said:**
> Ubuntu One...

[https://ubuntuone.com/plans/](https://ubuntuone.com/plans/)

$10.00 (USD) per month >> This is what makes the project commercial ;)

In Canonical's defense, they need to find some way to get revenue to pay developers.  Everyone wins when Canonical is able to hire more developers.

Second, the Ubuntu distribution is still free in every sense of the term.  

Third, another freedom seldomly discussed is the freedom to run commercial software on your OS if you need to for some reason.  Canonical bringing such people that freedom in an easy way is a good thing in my opinion.

So I still think the AppStore is a good idea for the above people.  People who want to only worry about free software and nothing else can still run vanilla Ubuntu and be just fine.

PS. They say there is no AppStore, but having a central place where you can buy commercial applications sounds like an AppStore to me.  But again, I like the idea.

---

### Post by davideotape on 2009-05-26
> **whoop said:**
> Landscape....

I **am** glad that there are discussions about open sourcing launchpad :D

As far as I know landscape it is a seperate project from ubuntu. I'm probbably coming across as over optimistic here, but I don't think ubuntu is becoming comercial, and I don't beleive it ever will.

---

### Post by whoop on 2009-05-26
> **davideotape said:**
> But there's a free option. And they're not marketing it in our faces. It's offering a service, that they couldn't really offer for free otherwise.

I have no problem paying for a service. But if it's free, where is the source code?

---

### Post by Slug71 on 2009-05-26
This freakin blows!!:mad:

Like others have said, there are a few distros out there already using Packagekit and more looking into adopting it. Its  development is moving at a good pace and will continue to do so. 

Why not rather bring features from AppCenter and integrate them with Packagekit instead of vice versa so that Packagekit can continue to improve yet giving Ubuntu that edge??

Afterall its already in Kubuntu.

As also pointed out already, the resources to do this from scratch with the possibility of it failing seems like a waist when there are other things that could benefit.

---

### Post by davideotape on 2009-05-26
> **whoop said:**
> Mark Shuttleworth is talking about making Ubuntu One a default part of the Ubuntu desktop experience if I am not mistaken.

I haven't heard about that :S Do you have citation? And as long as the program doesn't advertise the paid option then I welcome this. But as soon as they start advertising I am fully against it's integration.

---

### Post by binbash on 2009-05-26
It does not matter even it is 0.0000000000000001$ /per year.That is commercial.

---

### Post by whoop on 2009-05-26
> **davideotape said:**
> I haven't heard about that :S Do you have citation? And as long as the program doesn't advertise the paid option then I welcome this. But as soon as they start advertising I am fully against it's integration.

[http://www.youtube.com/watch?v=t3PJPYWtJ9o](http://www.youtube.com/watch?v=t3PJPYWtJ9o)

---

### Post by davideotape on 2009-05-26
> **Slug71 said:**
> This freakin blows!!:mad:

Like others have said, there are a few distros out there already using Packagekit and more looking into adopting it. Its  development is moving at a good pace and will continue to do so. 

Why not rather bring features from AppCenter and integrate them with Packagekit instead of vice versa so that Packagekit can continue to improve yet giving Ubuntu that edge??

Afterall its already in Kubuntu.

As also pointed out already, the resources to do this from scratch with the possibility of it failing seems like a waist when there are other things that could benefit.

Some people are making really great points now. Shame it's too late. I think that topics mentioning the main points at uds should have been posted a week in advance so they could have been discussed here and so feedback from the forums could be relayed to those at uds. I'll work on getting threads up tomorrow for the remaining topics if that's okay for everyone :)

---

### Post by whoop on 2009-05-26
> **davideotape said:**
> As far as I know landscape it is a seperate project from ubuntu. I'm probbably coming across as over optimistic here, but I don't think ubuntu is becoming comercial, and I don't beleive it ever will.

I wouldn't like it if every "separate project" from Canonical is closed source and/or service fee based, or even free service based ([http://cultofmac.com/gnu-founder-warns-cloud-computing-is-a-trap/3332](http://cultofmac.com/gnu-founder-warns-cloud-computing-is-a-trap/3332)). I define "separate project" as something that Canonical develops from scratch, like landscape, launchpad, Ubuntu One, AppCenter etc.

---

### Post by davideotape on 2009-05-26
> **whoop said:**
> I wouldn't like it if every "separate project" from Canonical is closed source and/or service fee based. I define "separate project" as something that Canonical develops from scratch, like landscape, launchpad, Ubuntu One, AppCenter etc.

I would be a bit hacked off if that happened too, and I certainly think launchpad and ubuntu one should be opensourced. But I'm not bothered about the servie fee. Do people not realise that there is a free version of ubuntu one? And your average joe doesn't need more than 2GB of online storage.

---

### Post by whoop on 2009-05-26
> **davideotape said:**
> I would be a bit hacked off if that happened too, and I certainly think launchpad and ubuntu one should be opensourced. But I'm not bothered about the servie fee. Do people not realise that there is a free version of ubuntu one? And your average joe doesn't need more than 2GB of online storage.

[http://cultofmac.com/gnu-founder-warns-cloud-computing-is-a-trap/3332](http://cultofmac.com/gnu-founder-warns-cloud-computing-is-a-trap/3332)
It may seem far fetched, but there is truth in that story I think.

---

### Post by davideotape on 2009-05-26
> **whoop said:**
> [http://cultofmac.com/gnu-founder-warns-cloud-computing-is-a-trap/3332](http://cultofmac.com/gnu-founder-warns-cloud-computing-is-a-trap/3332)
It may seem far fetched, but there is truth in that story I think.

That raises a very good point, that I had not thought about. Being a relative computer geek, I know that if google goes bust i've lost my emails. That's why I don't use it for anything important, and am considering setting up my own mail server. But your average joe doesnt realize the implications at all. I think you may just have changed my opinion on ubuntu one integration woop ;)

---

### Post by whoop on 2009-05-26
> **davideotape said:**
> That raises a very good point, that I had not thought about. Being a relative computer geek, I know that if google goes bust i've lost my emails. That's why I don't use it for anything important, and am considering setting up my own mail server. But your average joe doesnt realize the implications at all. I think you may just have changed my opinion on ubuntu one integration woop ;)

Happy to add to global paranoia, within years our computers will be mere web browsers with BIOS operating systems ;) (actually that's quite possible)
Don't tell anyone but I've been known to install proprietary nvidia drivers on some machines :p:D](*,)

---

### Post by zekopeko on 2009-05-26
> **davideotape said:**
> That raises a very good point, that I had not thought about. Being a relative computer geek, I know that if google goes bust i've lost my emails. That's why I don't use it for anything important, and am considering setting up my own mail server. But your average joe doesnt realize the implications at all. I think you may just have changed my opinion on ubuntu one integration woop ;)

I get the feeling that you don't understand how ubuntu one works.
it simply mirrors the data on your computer to the cloud so that you have access to it from anywhere (w/ an internet connection).
The data is still on your computer.

And about emails. No service can guarantee 100% data safety. I wager that data on your computer is far more in danger of being lost the when it's in the "cloud" since most services automatically backup the data to 2 or more storage devices. i think gmail keeps 3 copies of your mailbox on goggle's servers. their whole filesystem is based on data redundancy.

---

### Post by zekopeko on 2009-05-26
> **whoop said:**
> I wouldn't like it if every "separate project" from Canonical is closed source and/or service fee based, or even free service based ([http://cultofmac.com/gnu-founder-warns-cloud-computing-is-a-trap/3332](http://cultofmac.com/gnu-founder-warns-cloud-computing-is-a-trap/3332)). I define "separate project" as something that Canonical develops from scratch, like landscape, launchpad, Ubuntu One, AppCenter etc.

so money shouldn't be made with ubuntu?

and gnu founder also thinks that "compressing" (shortening names of functions and variables) javascript for bandwidth savings is code obfuscation.
RMS is a fanatical idealist who sometimes get's lost in his ideals to the point of halting progress.

---

### Post by inportb on 2009-05-26
Hang on a sec... minifying and gzipping Javascript is bad? wtf is going on? :O

---

### Post by davideotape on 2009-05-26
> **zekopeko said:**
> I get the feeling that you don't understand how ubuntu one works.
it simply mirrors the data on your computer to the cloud so that you have access to it from anywhere (w/ an internet connection).
The data is still on your computer.

And about emails. No service can guarantee 100% data safety. I wager that data on your computer is far more in danger of being lost the when it's in the "cloud" since most services automatically backup the data to 2 or more storage devices. i think gmail keeps 3 copies of your mailbox on goggle's servers. their whole filesystem is based on data redundancy.

But I have control over what's on my server and who can access it. For all google cares they could just delete all gmail accounts, all the emails and all the backups. I am not opposed to ubuntu one as such, I am just opposed to some of the ways that it might be implemented/advertised to your average joe. For me it should be marketed as a memory stick replacement. End of. Unfortuantly I doubt this will be the case, but I still hope that the service adheres to the core ethos of ubuntu.

And I highly doubt that within years we'l all be using cloud computing,

---

### Post by whoop on 2009-05-26
> **zekopeko said:**
> so money shouldn't be made with ubuntu?

Sure anyone is entitled to make money. I just don't think that closed source, fee based, service/cloud based stuff should be a focus for a linux distro. And I know it's not that big of a focus (we still have a wonderful distro) but just about everything that canonical has developed themselves is about that stuff.
> **zekopeko said:**
> 
and gnu founder also thinks that "compressing" (shortening names of functions and variables) javascript for bandwidth savings is code obfuscation.

I think there's some truth in that as well. Even if you find that totally ridiculous, that doesn't mean everything he has to say is ridiculous.
> **zekopeko said:**
> 
RMS is a fanatical idealist who sometimes get's lost in his ideals to the point of halting progress.
I know he's from another planet, but it certainly doesn't hurt having some "aliens" amongst us.

---

### Post by gnomeuser on 2009-05-26
I have been hoping for Ubuntu to clue in and join upstream since PackageKit just came out till now. I am tired of this game of saying upstream is king and then when we finally have a uniform way to install and manage packages where such functionality should take place along with well designed and translated tools that function across platform.. they ditch it after stinging us along for over a year.

This has a foul smell of Not Invented Here syndrome.

I can no longer use nor recommend Ubuntu, the path they have taken simply makes it impossible for me to trust that they would select solutions that would make supporting multiple distributions easy for those of us who need to do so. One should not underestimate how far it would go to not have to write the same guide for 6 different distros, something in many cases PackageKit would allow me to do with simple use of the mozilla plugin to get things installed if they are available. One click, regardless of the distro not that is pure awesome.

---

### Post by whoop on 2009-05-26
> **davideotape said:**
> 
And I highly doubt that within years we'l all be using cloud computing,

Your probably right (and I certainly hope so), but:
[http://www.elasticvapor.com/2009/03/computer-is-operating-system.html](http://www.elasticvapor.com/2009/03/computer-is-operating-system.html)
[http://www.pcworld.com/article/165124/the_future_is_bios_and_browsers.html](http://www.pcworld.com/article/165124/the_future_is_bios_and_browsers.html)
[http://www.pcauthority.com.au/News/130006,browser-replaces-os.aspx](http://www.pcauthority.com.au/News/130006,browser-replaces-os.aspx)
[http://www.linuxworld.com/news/2009/051909-the-future-is-bios-and.html?fsrc=rss-linux-news](http://www.linuxworld.com/news/2009/051909-the-future-is-bios-and.html?fsrc=rss-linux-news)

---

### Post by Regenweald on 2009-05-26
> **whoop said:**
> I'm probably the only one, but I find Ubuntu getting increasingly more "commercial". I have the feeling that this AppCenter is (at least partially) a money making scheme (soon it'll be an AppStore).
Not that I have problems with people trying to make money, but, not in the face :(

Sounds like you're going overboard a bit. An appstore to sell what exactly ? in the totally free GNU environment. I understand the disappointment of some members, but lets at LEAST wait to have something tangible to test before getting emotional.

---

### Post by psyke83 on 2009-05-26
> **Regenweald said:**
> Sounds like you're going overboard a bit. An appstore to sell what exactly ? in the totally free GNU environment. I understand the disappointment of some members, but lets at LEAST wait to have something tangible to test before getting emotional.

Don't be so naive. There are components such as media codecs (w32codecs) and decryption libraries (libdvdcss2) that can be licensed - in other words, a paid version of Medibuntu. There are also some closed-source programs available for Linux, such as Nero and others.

Note: don't take this as a criticism one way or another, just an observation.

---

### Post by whoop on 2009-05-26
> **Regenweald said:**
> Sounds like you're going overboard a bit. An appstore to sell what exactly ? in the totally free GNU environment. I understand the disappointment of some members, but lets at LEAST wait to have something tangible to test before getting emotional.
Did you read the rest of the thread? 
It surely still feels like a totally free GNU environment but there are an increasingly number of people who believe that the only way to make linux a real success is to commercialize it (at least in parts) in the long run. As I described in my previous posts in this thread.
Here's another one:
[http://www.youtube.com/watch?v=YoYL4R3Te2s](http://www.youtube.com/watch?v=YoYL4R3Te2s)

---

### Post by Regenweald on 2009-05-26
> **psyke83 said:**
> Don't be so naive. There are components such as media codecs (w32codecs) and decryption libraries (libdvdcss2) that can be licensed - in other words, a paid version of Medibuntu. There are also some closed-source programs available for Linux, such as Nero and others.

Note: don't take this as a criticism one way or another, just an observation.

But that honestly doesn't sound like much of an appstore does it ? An entire store with 10, 20, maybe 30 products ? all freely available elsewhere. A valid example you gave, but still not really 'next step' just 'obscure possibility'

---

### Post by psyke83 on 2009-05-26
> **gnomeuser said:**
> I have been hoping for Ubuntu to clue in and join upstream since PackageKit just came out till now. I am tired of this game of saying upstream is king and then when we finally have a uniform way to install and manage packages where such functionality should take place along with well designed and translated tools that function across platform.. they ditch it after stinging us along for over a year.

This has a foul smell of Not Invented Here syndrome.

I can no longer use nor recommend Ubuntu, the path they have taken simply makes it impossible for me to trust that they would select solutions that would make supporting multiple distributions easy for those of us who need to do so. One should not underestimate how far it would go to not have to write the same guide for 6 different distros, something in many cases PackageKit would allow me to do with simple use of the mozilla plugin to get things installed if they are available. One click, regardless of the distro not that is pure awesome.

Perhaps PackageKit will be adopted as the "backend". All I can suggest is that you cross your fingers and hope for the best ;).

I've noticed that you're a big fan of PackageKit, but let's be honest - it wasn't a perfect replacement of Synaptic in time for previous releases of Ubuntu. It caused some issues when I tested it on Fedora, too, and I heard a lot of complaints about it during the development process. 

But hey, that's ok! I'm sure it's been making steady improvements (and I'm interested in testing the [0.4.x series]("https://edge.launchpad.net/~packagekit/+archive/0.4.x") as soon as the packages successfully build). I would much prefer to see PackageKit in Fedora (as most bleeding-edge technologies are included first), and have it included into Ubuntu when it has reached a sufficient level of maturity and user-friendliness.

I wish that PulseAudio wasn't included in Hardy, for example. The version of ALSA shipped with Hardy had several critical issues with the PulseAudio ALSA plugins, which led to a suboptimal PulseAudio configuration being used. This caused sound mixing to break, and lots of people got pissed off at Lennart - unfairly.

---

### Post by psyke83 on 2009-05-26
> **Regenweald said:**
> But that honestly doesn't sound like much of an appstore does it ? An entire store with 10, 20, maybe 30 products ? all freely available elsewhere. A valid example you gave, but still not really 'next step' just 'obscure possibility'

They can easily mix it with free and non-free components. It makes sense when you think about it...

By the way, "freely available" does not always translate to "legal" in every country. Consider the recent events with Microsoft suing TomTom over FAT long filename patents.

---

### Post by Slug71 on 2009-05-26
> **davideotape said:**
> Some people are making really great points now. Shame it's too late. I think that topics mentioning the main points at uds should have been posted a week in advance so they could have been discussed here and so feedback from the forums could be relayed to those at uds. I'll work on getting threads up tomorrow for the remaining topics if that's okay for everyone :)

I think that is a really good idea. It appears they need feedback from the forum. Hopefully someone at UDS will be reading this thread and see how much they have dissapointed a lot of people. Perhaps some of the resources that could be waisted with AppCenter could now go to closing that useless Ubuntu Brainstorm. Just look at the support for Packagekit there. 

> **gnomeuser said:**
> I have been hoping for Ubuntu to clue in and join upstream since PackageKit just came out till now. I am tired of this game of saying upstream is king and then when we finally have a uniform way to install and manage packages where such functionality should take place along with well designed and translated tools that function across platform.. they ditch it after stinging us along for over a year.

This has a foul smell of Not Invented Here syndrome.

I can no longer use nor recommend Ubuntu, the path they have taken simply makes it impossible for me to trust that they would select solutions that would make supporting multiple distributions easy for those of us who need to do so. One should not underestimate how far it would go to not have to write the same guide for 6 different distros, something in many cases PackageKit would allow me to do with simple use of the mozilla plugin to get things installed if they are available. One click, regardless of the distro not that is pure awesome.

I feel very much the same and am seriously considering going to Super Ubuntu now. Last i knew they had Packagekit. 
For three/four versions now its been, next version, next version...., i mean seriously.

Just makes so much more sense to integrate AppCenter with Packagekit.

---

### Post by jsmidt on 2009-05-26
> **Slug71 said:**
> Hopefully someone at UDS will be reading this thread and see how much they have dissapointed a lot of people. Perhaps some of the resources that could be waisted with AppCenter could now go to closing that useless Ubuntu Brainstorm. Just look at the support for Packagekit there. 

Well, the conference is still in session for a few more days, so maybe someone will mention the thread.

However, I've watched Ubuntu for years.  I've been around for all their "controversial" ideas.  I remember fallout over not being binary compatible with Debian back in the day. (Anyone else been around long enough to remember that?)

Anyways, Ubuntu at the end of the day consistently produces a Linux distro that people are increasingly impressed with.  I really trust their judgment.  

However, if people want a Linux distro with no commercial ties and great (probably unparallelled) upstream support, try Fedora.

---

### Post by Merk42 on 2009-05-26
> **Slug71 said:**
> I feel very much the same and am seriously considering going to Super Ubuntu now. Last i knew they had Packagekit. 
For three/four versions now its been, next version, next version...., i mean seriously.

Oh, but who cares what the default is, I mean, you can change it easily anyway.

Not so funny when it's not just the theme anymore, is it? :D

---

### Post by jsmidt on 2009-05-26
> **jsmidt said:**
> 
However, if people want a Linux distro with no commercial ties and great (probably unparallelled) upstream support, try Fedora.

Before people criticize this statement saying: "No commercial ties? What about Red Hat?" let me just say from personal experience: Red hat sponsors Fedora, but Fedora has no hint of commercial software anywhere in the archives and everyting is free in every sense of the world. 

 My point is you don't see any commercialism inside Fedora even though Red Hat supports it.

---

### Post by ktp on 2009-05-26
> **Merk42 said:**
> Oh, but who cares what the default is, I mean, you can change it easily anyway.

Not so funny when it's not just the theme anymore, is it? :D

hehe...made my day!! :D

---

### Post by ktp on 2009-05-26
> **gnomeuser said:**
> I have been hoping for Ubuntu to clue in and join upstream since PackageKit just came out till now. I am tired of this game of saying upstream is king and then when we finally have a uniform way to install and manage packages where such functionality should take place along with well designed and translated tools that function across platform.. they ditch it after stinging us along for over a year.

I have to agree...I mean one of the whole issue with Linux app is different distribution has its "own way" to install app.  (Not that I totally agree with [Linux's dirty little secret ]("http://blogs.zdnet.com/hardware/?p=2144") but does make its point)

The whole idea with PackageKit is to "unify all the software graphical tools used in different distributions, and use some of the latest technology like PolicyKit to make the process suck less."  At least this is trying to unify a way to add/remove software...making it easy for "windows user".  It does not solve all the issues but it is a good start.  Lets hope AppCenter really considers it.

---

### Post by zekopeko on 2009-05-26
> **jsmidt said:**
> Before people criticize this statement saying: "No commercial ties? What about Red Hat?" let me just say from personal experience: Red hat sponsors Fedora, but Fedora has no hint of commercial software anywhere in the archives and everyting is free in every sense of the world. 

 My point is you don't see any commercialism inside Fedora even though Red Hat supports it.

you are missing one crucial point: ubuntu doesn't have a commercial distro and a community distro. ubuntu is a community project and commercial if you choose to buy support.
and if you think that including ubuntuone client is a problem, i hope that you aren't using facebook,twitter,gmail,Google(anything).

---

### Post by Slug71 on 2009-05-26
> **Merk42 said:**
> Oh, but who cares what the default is, I mean, you can change it easily anyway.

Not so funny when it's not just the theme anymore, is it? :D


Yes you can and i do but its a a lot different than if it was default. All the way to upsteam.

A theme is a theme and cant be compared to package management.

---

### Post by jsmidt on 2009-05-26
a

---

### Post by jsmidt on 2009-05-26
> **zekopeko said:**
> you are missing one crucial point: ubuntu doesn't have a commercial distro and a community distro. ubuntu is a community project and commercial if you choose to buy support.
and if you think that including ubuntuone client is a problem, i hope that you aren't using facebook,twitter,gmail,Google(anything).


I don't think you understood my thread.  I support UbuntuOne, cloud computing and an AppStore if such a thing actually happens.  I was trying to tell those who don't like such things Fedora is a great alternative to Ubuntu if they can't stand commercial ties within a distribution.  

But for most people, commercial ties are a good thing, not a bad, so I think Ubuntu is making the right decisions with these things.

---

### Post by Kareeser on 2009-05-26
What I'm getting here (and I could be seeing this wrong), is that the people who are against the "AppStore" are threatened because they feel as though developers will be pursuaded by the evil lure of money to develop their programs for monetary gain, eventually slowing all open-source development to a halt, as all of our favourite programs turn closed-source, OR, alternatively, that a "brain drain" occurs, and we lose our best and brightest developers to mindless closed-source corporations, leaving a bunch of amateur hackers and programmers to muck about with the source code and add easter eggs instead of functionality.

However, what you have forgotten is that that environment _already exists_ in the manifestation of Windows and OS X. If our devs wanted to work for money, they would... and many of them DO, but they contribute to free software because it's free, not because they don't have anything else to do.

+1 for AppStore here.

---

### Post by psyke83 on 2009-05-26
> **Kareeser said:**
> What I'm getting here (and I could be seeing this wrong), is that the people who are against the "AppStore" are threatened because they feel as though developers will be pursuaded by the evil lure of money to develop their programs for monetary gain, eventually slowing all open-source development to a halt, as all of our favourite programs turn closed-source, OR, alternatively, that a "brain drain" occurs, and we lose our best and brightest developers to mindless closed-source corporations, leaving a bunch of amateur hackers and programmers to muck about with the source code and add easter eggs instead of functionality.

However, what you have forgotten is that that environment _already exists_ in the manifestation of Windows and OS X. If our devs wanted to work for money, they would... and many of them DO, but they contribute to free software because it's free, not because they don't have anything else to do.

+1 for AppStore here.

Yes I totally agree, the presence of Windows and Mac OS X prevented Mandrake from becoming a commercialized distribution - Mandriva, and it's popularity totally sustained itself when this occurred. We have nothing to worry about, of course.

---

### Post by ronacc on 2009-05-26
I have no gripe with propriatary software , I use it when it is the best for the job in my opinion . I have no gripe with the appstore , I would buy some myself if there was one that offered me substantial advantages over the foss apps for the same job . my gripe is with packagekit itself at this point in its developement . The promises made for PK would be welcome if realised but so far it has shown me nothing that makes me believe it its anywhere near ready for prime time . To make it the default for anything at this point would be a serious mistake.

---

### Post by Slug71 on 2009-05-27
> **ronacc said:**
>  The promises made for PK would be welcome if realised but so far it has shown me nothing that makes me believe it its anywhere near ready for prime time . To make it the default for anything at this point would be a serious mistake.

Sure it needs improvement but its moving along. 
With other Distros hopping on board and contributing to it, it will only move along better and faster though.
Picture where Packagekit may be a year from now and Ubuntu could have made it unique by adding the AppCenter stuff to it instead of going at something alone.

I dont see how this will benefit Ubuntu anytime soon.

---

### Post by mpt on 2009-05-27
> **psyke83 said:**
> Because PackageKit already exists beyond a concept phase?

gnome-app-install already exists too, and it is several years more mature than PackageKit is.

> *Because Fedora (and most likely, other distributions) seem to be moving towards adoption in the same way as PulseAudio was?*

I don’t think using PulseAudio as an example strengthens your argument, really. :D

> *Because contributing to a cross-distribution project (instead of a project intended only for a single distribution) will increase good-will between ourselves and upstream, as well as other distributions?*

What other OSes are doing is one factor, but not the only factor. And “upstream” does not mean “whatever Fedora does”. The Fedora developers do a lot of important and valuable work, but Ubuntu has millions of non-technical users to care about, which Fedora does not.

> *If you "modularize" AppCenter so that it can use a vanilla PackageKit backend (or at least introduce changes that upstream would like to use themselves), then you can maintain full control over the development process, rather than find yourself limited by upstream.*

So you think the problem with [this diagram]("http://algebraicthunk.net/~dburrows/blog/entry/apt-system-diagram/") is that it just doesn’t have enough layers? ;)

Seriously, though, “limited by upstream” means the opposite of what you seem think it does. For example, one thing we’ve discussed is making changes to components as low-level as dpkg itself, so that the progress bar when installing or uninstalling software can be smoother than it is now. If we had to do things like that through a PackageKit layer, or — even worse — through an abstraction layer that was itself calling PackageKit, it would be much harder to achieve.

> **gnomeuser said:**
> I have been hoping for Ubuntu to clue in and join upstream since PackageKit just came out till now. I am tired of this game of saying upstream is king and then when we finally have a uniform way to install and manage packages where such functionality should take place along with well designed and translated tools that function across platform.. they ditch it after stinging us along for over a year.

With respect, gnomeuser, the only person I’ve seen “stringing us along” about PackageKit is you, here, in the Ubuntu Forums. Actual Ubuntu developers have consistently been clear, in UDS sessions and [elsewhere]("https://wiki.ubuntu.com/DesktopTeam/Specs/PackageKit#Outstanding%20Issues"), about PackageKit’s shortcomings. And actual PackageKit developers have similarly been clear about their unwillingness to address some of those shortcomings. It’s a healthy and understandable disagreement, but it’s still a disagreement.

Again, it is quite possible we will adopt some PackageKit code. But if we adopted PackageKit wholesale, we would likely need to fork it to address those shortcomings. I doubt that would make you any happier.

> *One should not underestimate how far it would go to not have to write the same guide for 6 different distros…*

If you are writing guides for “distros”, you are Doing It Wrong.

---

### Post by ghindo on 2009-05-27
Thank you for clearing some things up, mpt.  I think your post helped me better understand the reasoning process behind the AppCenter decision making process.

---

### Post by psyke83 on 2009-05-27
> **mpt said:**
> gnome-app-install already exists too, and it is several years more mature than PackageKit is.
True, but it's tied to GNOME/GTK. PackageKit has frontends for QT and GTK, so that's an advantage when considering the fate of Kubuntu.

> I don&#8217;t think using PulseAudio as an example strengthens your argument, really. :D
;) True. However, a case can be made that Ubuntu tends to adopt new technologies either too soon (PulseAudio), or too late (arguably PackageKit for Karmic, but it remains to be seen if the AppCenter will replace it in terms of functionality).

> What other OSes are doing is one factor, but not the only factor. And &#8220;upstream&#8221; does not mean &#8220;whatever Fedora does&#8221;. The Fedora developers do a lot of important and valuable work, but Ubuntu has millions of non-technical users to care about, which Fedora does not.

I concede your point about Fedora and Ubuntu having different audiences to cater for. My point was that if PackageKit 0.4.x could serve as a user-friendly replacement for update-manager, Add/Remove Programs and Synaptic, it should be adopted without argument. My testing of the older 0.3 series led me to believe that it wasn't ready, but perhaps the latest version is ready.

> So you think the problem with [this diagram]("http://algebraicthunk.net/~dburrows/blog/entry/apt-system-diagram/") is that it just doesn&#8217;t have enough layers? ;)

Funny. However, the PackageKit framework and PackageKit frontends are presumably developed in unison, so this shouldn't be a cause for concern. It's not really adding extra layers of complexity; it's just a frontend. 

Do you complain that file-roller relies on command-line archivers to function? No, because it works well. PackageKit's core framework is presumably agnostic to UI environments (QT/KDE), which has distinct advantages. In comparison, I would imagine that gnome-app-install needs some GNOME or GTK libraries to function on a KDE system.


> Seriously, though, &#8220;limited by upstream&#8221; means the opposite of what you seem think it does. For example, one thing we&#8217;ve discussed is making changes to components as low-level as dpkg itself, so that the progress bar when installing or uninstalling software can be smoother than it is now. If we had to do things like that through a PackageKit layer, or &#8212; even worse &#8212; through an abstraction layer that was itself calling PackageKit, it would be much harder to achieve.

I meant PackageKit's core developers when I referred to upstream, not Debian (which would represent Ubuntu's "general" first-level upstream source). You're talking about changing Debian's upstream code when you're thinking of modifying dpkg. If you change dpkg, surely you'll change apt to take advantage of new features. If this happens (without Debian going insane, but that's another matter), PackageKit will surely adapt itself. 

> Again, it is quite possible we will adopt some PackageKit code. But if we adopted PackageKit wholesale, we would likely need to fork it to address those shortcomings. I doubt that would make you any happier.

This is what I meant about being constrained by upstream; judging from what you wrote, it seems likely that you will feel constrained, so perhaps it's better not to use PackageKit as a component for AppCenter.

However, if AppCenter ends up as an imitation of PackageKit (perhaps with some superficial changes), we're not going to make any friends in the wider open-source community. Forking or reimplementing an application differently can be a good thing, but not if it's because of a "not-invented-here" mindset.

---

### Post by jsmidt on 2009-05-27
> **ghindo said:**
> Thank you for clearing some things up, mpt.  I think your post helped me better understand the reasoning process behind the AppCenter decision making process.

+1  Thanks MPT.   Your commentary is really helpful.  You are one of the few people close enough to the action to really know what you are talking about.

---

### Post by Regenweald on 2009-05-27
I love that the decision makers actually care what goes on in the forums! Thank you MPT, until I upgrade to Karmic Testing, i'll stick to the wait and see approach.

---

### Post by Swarms on 2009-05-27
In a longer perspective, I hope they pick the solution, which is going to be used across the board, KDE and Gnome distrobutions alike.

---

### Post by Sophont on 2009-05-27
I'll wait and see.

For people already using Ubuntu I don't see what the big deal is.

Synaptic, Add/Remove and UpdateManager work well and do the trick well enough.

For new user I can see the value of improving several parts and doing this as a cross-distro development would be a good thing.
But if Ubuntus developers think they need to do appcenter instead I trust that they have their reasons. If those reasons turn out to be bad - PackageKit is still there and so are the established tools.
Also note that most of the appcenter goals are about UI functionality. As long as PackageKit supports the required functionality it could be used as the model layer with just a thin UI layer on top - making appcenter porttable to all PackageKit environments for free.
If PackageKit does not support all the required functionality imagined for appcenter (and can't easily patched to get there) - then I guess we know why the devs saw a reason to do yet another package app.

What I would *love* to see is a unified package format adopted by all distros.
I don't see any value in having deb and rpm both.
Something like PackageKit might help to get there because having a unified layer makes the package format less important to the user and hopefully reduces irrational preferences.

With regard to commercializing Ubuntu - what exactly seems to be the problem here?
Canonical has been a commercial outfit to begin with.
That Linux/GNU/FLOSS software is developed by just/mostly selfless devs is a myth to begin with. This software is the result of a mixed ecosystem with a lot of commercial interests behind it. Sure - there are lots of people who invest unpaid hours into writing patches, writing/triaging bug reports etc... Some do so because it fixes a bug that annoys them, others as part of university projects. But a lot of the work done is financed directly or indirectly by the major Linux players (IBM, RH, Novell, Sun, Google, Intel, etc...). They all have their reasons - all for profit eventually. Be it to sell server hardware, services, strategic weakening of a competitor (MS) etc...

And that's good and healthy. Full time devs need to make money just as anybody else. And without them we wouldn't have what we have now.

If Canonical expands it's commercial partner offerings (a few have been there for ages already) and markets a full blown "app store" - how is that a bad thing? Nobody *has* to buy stuff. Being offered stuff that I then might *want* to buy is a good thing.

If Valve would start supporting Steam on e.g. Ubuntu figuring that amongst its 10 million users is sufficient additional sale potential that alone would be a revolution in Linux adoption. Games are the biggest hindrance for regular users (many of whom also like to play games). Average joe already finds all daily needs covered by a default Ubuntu install (browser, word processor, media player - what else do Joe and Jane use actually? - make a legal codec package available for 10-20 bucks and all is wonderful).
Most users never need Photoshop. Gimp is overkill for them.

The one thing a lot of people complain about is that they still need to boot WXP/Vista to play PC games.

(Another big group is business with legacy windows software dependencies - but that market has very different rules).

In short I welcome commercial "offerings". As long as I don't get forced into everything (and Canonical made a pledge to keep Ubuntu free forever), being offered the *option* of easily buying stuff is a good thing.

---

### Post by xebian on 2009-05-27
> :Sophont: What I would *love* to see is a unified package format adopted by all distros.
I don't see any value in having deb and rpm both.

Dream on.  And what should it be?

---

### Post by davideotape on 2009-05-27
> **xebian said:**
> Dream on.  And what should it be?

drepbm? :)

---

### Post by Gourgi on 2009-05-27
> **xebian said:**
> Dream on.  And what should it be?

.bin (or .exe) :p

---

### Post by davideotape on 2009-05-27
> **Gourgi said:**
> (or .exe)

:lolflag:

---

### Post by mpt on 2009-05-27
> **psyke83 said:**
> True, but it's tied to GNOME/GTK. PackageKit has frontends for QT and GTK, so that's an advantage when considering the fate of Kubuntu.

Kubuntu’s plans are up to the Kubuntu developers.

> *My point was that if PackageKit 0.4.x could serve as a user-friendly replacement for update-manager, Add/Remove Programs and Synaptic, it should be adopted without argument.*

Not necessarily.

> *Do you complain that file-roller relies on command-line archivers to function? No, because it works well.*

Yes, actually, I do — because that means file-roller shows an uninformative bouncing progress bar, instead of showing actual determinate progress and an estimate of time remaining for large archives. Now, the command-line archiving utilities could — and perhaps should — be modified to have flags to show that determinate progress and time remaining, and then file-roller could be modified to use those flags and parse that output, but now you have *n* bits of software to modify rather than one, so people haven’t bothered to do it. It’s a textbook example of what I call [mediocrity through modularity]("http://mpt.net.nz/archive/2008/08/01/free-software-usability#modularity").

> *If you change dpkg, surely you'll change apt to take advantage of new features. If this happens (without Debian going insane, but that's another matter), PackageKit will surely adapt itself.*

“Surely”? Why would the PackageKit developers bother to add features that only one packaging format supported? And even if they did, how much longer would it take?

> *However, if AppCenter ends up as an imitation of PackageKit (perhaps with some superficial changes), we're not going to make any friends in the wider open-source community.*

I have no intention of designing AppCenter to look like PackageKit. :)

---

### Post by aamukahvi on 2009-05-27
> **mpt said:**
> Yes, actually, I do &#8212; because that means file-roller shows an uninformative bouncing progress bar, instead of showing actual determinate progress and an estimate of time remaining for large archives. Now, the command-line archiving utilities could &#8212; and perhaps should &#8212; be modified to have flags to show that determinate progress and time remaining, and then file-roller could be modified to use those flags and parse that output, but now you have *n* bits of software to modify rather than one, so people haven&#8217;t bothered to do it. It&#8217;s a textbook example of what I call [mediocrity through modularity]("http://mpt.net.nz/archive/2008/08/01/free-software-usability#modularity").
Well that's a stupid behaviour, one that a proper *modular* design would fix. Fileroller should use the respective compression libraries, not the CLI apps. I think there is a libpackagekit that the different frontends use?

---

### Post by 23meg on 2009-05-27
I've edited the original title of the thread, which was misleading.

---

### Post by psyke83 on 2009-05-27
> **aamukahvi said:**
> Well that's a stupid behaviour, one that a proper *modular* design would fix. Fileroller should use the respective compression libraries, not the CLI apps. I think there is a libpackagekit that the different frontends use?

Indeed. Most of the command-line tools support detailed progress indicators, though. For example, rar is "-vt" (verbose - technical), 7z uses progressbars by default, etc. This is merely laziness on the part of the file-roller frontend.

The argument is a little thin since PackageKit and its frontends are developed in unison, so presumably this "mediocrity through modularity" doesn't necessarily exist.

---

### Post by Kareeser on 2009-05-27
Any news on the UDS front today?

---

### Post by Slug71 on 2009-05-27
> **mpt said:**
> gnome-app-install already exists too, and it is several years more mature than PackageKit is.



I don’t think using PulseAudio as an example strengthens your argument, really. :D



What other OSes are doing is one factor, but not the only factor. And “upstream” does not mean “whatever Fedora does”. The Fedora developers do a lot of important and valuable work, but Ubuntu has millions of non-technical users to care about, which Fedora does not.



So you think the problem with [this diagram]("http://algebraicthunk.net/~dburrows/blog/entry/apt-system-diagram/") is that it just doesn’t have enough layers? ;)

Seriously, though, “limited by upstream” means the opposite of what you seem think it does. For example, one thing we’ve discussed is making changes to components as low-level as dpkg itself, so that the progress bar when installing or uninstalling software can be smoother than it is now. If we had to do things like that through a PackageKit layer, or — even worse — through an abstraction layer that was itself calling PackageKit, it would be much harder to achieve.



With respect, gnomeuser, the only person I’ve seen “stringing us along” about PackageKit is you, here, in the Ubuntu Forums. Actual Ubuntu developers have consistently been clear, in UDS sessions and [elsewhere]("https://wiki.ubuntu.com/DesktopTeam/Specs/PackageKit#Outstanding%20Issues"), about PackageKit’s shortcomings. And actual PackageKit developers have similarly been clear about their unwillingness to address some of those shortcomings. It’s a healthy and understandable disagreement, but it’s still a disagreement.

Again, it is quite possible we will adopt some PackageKit code. But if we adopted PackageKit wholesale, we would likely need to fork it to address those shortcomings. I doubt that would make you any happier.



If you are writing guides for “distros”, you are Doing It Wrong.

Packagekit, Packagekit, Packagerkit!!!!!!!!!!!!!!!!!!!!!

---

### Post by xebian on 2009-05-27
> **aamukahvi said:**
> ... Fileroller should use the respective compression libraries, not the CLI apps. ...

???

---

### Post by xebian on 2009-05-27
[QUOTE=mpt;7354516]
Yes, actually, I do — because that means file-roller shows an uninformative bouncing progress bar, instead of showing actual determinate progress and an estimate of time remaining for large archives. Now, the command-line archiving utilities could — and perhaps should — be modified to have flags to show that determinate progress and time remaining, and then file-roller could be modified to use those flags and parse that output, but now you have *n* bits of software to modify rather than one, so people haven’t bothered to do it. It’s a textbook example of what I call [mediocrity through modularity]("http://mpt.net.nz/archive/2008/08/01/free-software-usability#modularity").


/QUOTE]

How much fancier CLI apps could be?  Archiving utilities just do what they do best and then exit with a status of success or fail.  If you want to front-end it, then it's your job to present to your user those fancy file status if you want.  And they use file utilities to do that.

If this is your understanding of this process, then I won't be surprised if the resulting UI is what you said yourself "textbook example ..."

Changing the backend because it doesn't jive with my front-end UI design is like the tail wagging the dog.

Cheers.

---

### Post by aamukahvi on 2009-05-27
>  Originally Posted by aamukahvi  View Post
... Fileroller should use the respective compression libraries, not the CLI apps. ...
> **xebian said:**
> ???

Just sayin'. The functionality that these compression applications use should be in libraries (and probably is) for easy reuse. So obviously Fileroller should depend on the libraries, not the CLI applications.

Now, for the reason it is done this way: it's probably easier to just pass some command line arguments to external executables than to do it "properly".

---

### Post by xebian on 2009-05-27
> **aamukahvi said:**
> Just sayin'. The functionality that these compression applications use should be in libraries (and probably is) for easy reuse. So obviously Fileroller should depend on the libraries, not the CLI applications.

Now, for the reason it is done this way: it's probably easier to just pass some command line arguments to external executables than to do it "properly".

hmmm,  ok I know now.;)

---

### Post by mpt on 2009-05-27
> **xebian said:**
> Changing the backend because it doesn't jive with my front-end UI design is like the tail wagging the dog.

To you, perhaps. But to others, the user experience is the most important thing. This is hardly an unusual view: apt itself, filesystem extended attributes, usplash, PolicyKit, the Completely Fair Scheduler, kernel mode setting, and DeviceKit-Power are all examples where the “back end” of a particular feature has been changed to allow better UI designs.

---

### Post by apoclypse on 2009-05-27
> **cszikszoy said:**
> Have any of you really used packagekit?  I know it sounds great on paper, but believe me, ubuntu's "Add/Remove" is light years ahead in terms of usability and understandability.  Packagekit may very well be the way to go, but I'm glad the decision was made to hold off for now.

I 100% agree. Everyone here seems to be touting PackageKit but Ubuntu has been doing what Packagekit does now for several releases already. Easy updates with intuitive UI, done, Easy to use package manager, done. More robust package manager for experienced users, done. Prompts for installing codecs, plugins, tools, done. Packagekit adds little to no benefit to the equation especially when the UI is mediocre and badly implemented, imo. Using Packagekit as a backend is fairly useless, imo. Apt-get at its core is speedy, is robust and already has great killer tools and developers who know how to develop tools for it, why add another layer if its not really necessary. What are the benefits to Packagekit over what Ubuntu offers now? I see very little to no benefit at the moment, when that changes then Ubuntu should revisit package kit, but a friendly updater, and a user friendly package manager has been in Ubuntu for quite some time, no need to drop what is already there for something that imo is inferior at the moment, 

With this being added to the equation you can be sure that Canonical will be way ahead of the game when it comes to installing and managing software on their distro. 

The sole reason I have stuck with Ubuntu this long is because of how easy it is to install software and easy it is to add external repos to use. Packagekit in Fedora is pretty damn clunky a a serious regression for Ubuntu, imo.

---

### Post by apoclypse on 2009-05-27
> **mpt said:**
> 

I have no intention of designing AppCenter to look like PackageKit. :)


Thank the lord for that. Packagekit is fugly and unintuitive, imo.

---

### Post by ktp on 2009-05-27
> **Gourgi said:**
> .bin (or .exe) :p

:lolflag:

---

### Post by ktp on 2009-05-27
> **Slug71 said:**
> Packagekit, Packagekit, Packagerkit!!!!!!!!!!!!!!!!!!!!!

Good luck, Good luck, Good luck!!! :lolflag:

I do hope it is seriously considered, but it doesn't look good when you have comments like this:

> **mpt said:**
> Kubuntu’s plans are up to the Kubuntu developers.

Now if we wanted to have same experience in all flavors of Ubuntu (forget other Linux distributions) then it might be different story.  :p

---

### Post by ktp on 2009-05-27
> **mpt said:**
> To you, perhaps. But to others, the user experience is the most important thing. This is hardly an unusual view: apt itself, filesystem extended attributes, usplash, PolicyKit, the Completely Fair Scheduler, kernel mode setting, and DeviceKit-Power are all examples where the “back end” of a particular feature has been changed to allow better UI designs.

I have to agree...UI is the what the user see and interact with so it has to be easy and good looking.  :p  And if that means backend needs to be modified/updated to help the front-end, then new API should be added to backend.  They go together; to some point.  But you can't just mix both if you want modular model, which is really important in Linux since there are different end users here: one who wants UI only, one who wants terminal only (hack even windows had to "improve" this for admins), and others who want mix of both world.

---

### Post by Slug71 on 2009-05-27
[[IMG]http://brainstorm.ubuntu.com/idea/64/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/64/)


Pshhh, i guess Brainstorm is just a waste of time considering the support for Packagekit there.

---

### Post by ktp on 2009-05-27
> **Slug71 said:**
> [[IMG]http://brainstorm.ubuntu.com/idea/64/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/64/)


Pshhh, i guess Brainstorm is just a waste of time considering the support for Packagekit there.

Wonder what this means...if anything:

> This idea was marked as being in development the 4 June 08. Target release: Ubuntu 9.10 Karmic Koala.

I guess in this case considered but not really developed?

---

### Post by jsmidt on 2009-05-27
> **Slug71 said:**
> [[IMG]http://brainstorm.ubuntu.com/idea/64/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/64/)


Pshhh, i guess Brainstorm is just a waste of time considering the support for Packagekit there.

Slug71, I admire your passion.  I was wondering, now that you have read about the AppCenter from various sources, what about PackageKit specifically do you think would make it better?

---

### Post by ktp on 2009-05-27
> **jsmidt said:**
> Slug71, I admire your passion.  I was wondering, now that you have read about the AppCenter from various sources, what about PackageKit specifically do you think would make it better?

I am not Slug71...but I had found this very interesting when I first read it about PackageKit (little old but great)

[http://people.freedesktop.org/~hughsient/public/introduction-to-packagekit.pdf](http://people.freedesktop.org/~hughsient/public/introduction-to-packagekit.pdf)

---

### Post by xebian on 2009-05-27
> **mpt said:**
> To you, perhaps. But to others, the user experience is the most important thing. This is hardly an unusual view: apt itself, filesystem extended attributes, usplash, PolicyKit, the Completely Fair Scheduler, kernel mode setting, and DeviceKit-Power are all examples where the “back end” of a particular feature has been changed to allow better UI designs.

When a project has a backend and frontend parts it may make sense.  But when you front long established archiving utilities it's a hard sell to say tar or gzip to change just to accomodate FileRoller.  Archiving utilities are designed for speed and/or tight compression ratios.  They can't hold and stop their main function just to satisfy your "Are we there yet?" querry.  Like I said earlier there are excellent file utilities for this purpose.

---

### Post by Slug71 on 2009-05-27
> **jsmidt said:**
> Slug71, I admire your passion.  I was wondering, now that you have read about the AppCenter from various sources, what about PackageKit specifically do you think would make it better?

One of the main things i like about Packagekit is the development progress of it. Just look how much it has evolved over the last year. A few Distros already have it as default and there are more looking into adopting it and therefore it will continue its good rate of progress and do so with stability.

These are some C/Ps from another thread of why i like Packagekit too.

 > What PackageKit gives us is a unified interface for other software to achieve software installation tasks. For example, Totem's automatic codec install in Ubuntu is a somewhat distro-specific hack. It was done for PackageKit and now works anywhere. There are examples of Nautilus automatically finding and installing software to open files based on their MIME types.
The current glchess (Applications -> Games -> Chess) makes a really cryptic request for certain packages it needs for 3D mode. It's ugly, but that's the best it can do. With PackageKit, it could have a magical ability to select those for installation.

If I recall correctly, PackageKit is getting a web plugin to jump in to package installation from a web page!

It's not just an identical interface for you (which isn't actually true because you one jump in and modify the GUI); it's an identical interface for everyone, so software can consistently help with package management to make it easy for Grandma to install stuff.

> Yes, if the major distros adapt PackageKit, then KDE and Gnome applications can use PackageKit's interface/API to install software/codecs/etc. PK will get lots of exposure, and turn into a very stable product, and distros don't have to integrate their package system every release.

Application developers will only have to implement package management in their application once, and distributions will not have to modify this for their package system.

Summary:
So, it is not the equal graphical interface that is the largest benefit, but the time and frustration saved by application developers and distributions.


Therefore i think it would have been smarter to integrate AppCenter's stuff with PK making PK a little unique to Ubuntu/Kubuntu.
A lot less responsibilty for Canonical too instead of taking on something on their own from the ground up which could potentially fail.

---

### Post by jsmidt on 2009-05-27
> **Slug71 said:**
> 
Therefore i think it would have been smarter to integrate AppCenter's stuff with PK making PK a little unique to Ubuntu/Kubuntu.
A lot less responsibilty for Canonical too instead of taking on something on their own from the ground up which could potentially fail.

Slug71, do you like the mockups of AppCenter you see?  Are you only concerned about it as a backend?

---

### Post by Slug71 on 2009-05-27
> **jsmidt said:**
> Slug71, do you like the mockups of AppCenter you see?  Are you only concerned about it as a backend?

The mockups are ok but yes its just the backend or is it frontend that concerns me. But i guess only time will tell.

---

### Post by ranch hand on 2009-05-27
Slug71,
Don't get your knickers in too tight a knot, the world will not end for the lack of package kit.

As you can see from my sig, I am kind of interested in different OSs.  I had never really looked at Super OS (you refer to the old name).  I made the Ultimate Edition mistake and kind of turned me off to grandeous sounding Ubuntu varients.

I have to thank you for pointing it out again.

The gist of this is that I downloaded and installed the bugger.  I do not see any sign of packagekit.

It is a pretty nice OS from what I have seen of it.  I am on it now, exploring.

---

### Post by jsmidt on 2009-05-27
I personally install everything over a command line.  I do think it would be really useful if the AppCenter had a way to search via tags and key words.  It would be nice if, not knowing what the package is called, I could just type in the types of things I want the application to do, and it finds the best app for me.

For example, there was a thread the other day asking about the best LaTeX editor.  It would be nice to just search "LaTeX editor" and various suggestions pop up with user ratings.  Maybe some pros and cons about each package.

I also hope it detects things like codecs and tells you exactly what you need to install.

---

### Post by ktp on 2009-05-27
> **jsmidt said:**
> I personally install everything over a command line.  I do think it would be really useful if the AppCenter had a way to search via tags and key words.  It would be nice if, not knowing what the package is called, I could just type in the types of things I want the application to do, and it finds the best app for me.

For example, there was a thread the other day asking about the best LaTeX editor.  It would be nice to just search "LaTeX editor" and various suggestions pop up with user ratings.  Maybe some pros and cons about each package.

I also hope it detects things like codecs and tells you exactly what you need to install.

This sounds so much like what PK is trying to do/provides.  One thing that will not really fit into Ubuntu is the notifications used by PK.  PK has some really nice notification with user actions...which would turn into dialogs in the new ubuntu notification system.  Maybe this is not that bad...just will have to wait and see.

---

### Post by RAOF on 2009-05-27
> **jsmidt said:**
> I personally install everything over a command line.  I do think it would be really useful if the AppCenter had a way to search via tags and key words.  It would be nice if, not knowing what the package is called, I could just type in the types of things I want the application to do, and it finds the best app for me.

For example, there was a thread the other day asking about the best LaTeX editor.  It would be nice to just search "LaTeX editor" and various suggestions pop up with user ratings.  Maybe some pros and cons about each package.

Welcome to [DebTags]("http://debtags.alioth.debian.org/faq.html").  Plus, to be fair, some additional infrastructure for the pros/cons.

> **jsmidt said:**
> 
I also hope it detects things like codecs and tells you exactly what you need to install.
That'd be in [scope](https://wiki.ubuntu.com/AppCenter), yes.

---

### Post by jsmidt on 2009-05-28
> **RAOF said:**
> Welcome to [DebTags]("http://debtags.alioth.debian.org/faq.html").  

Is DebTags already included into Ubuntu package management software?  If it is I didn't know about it.

---

### Post by Oak37 on 2009-05-28
AppCenter looks pretty good although I never had any problems using Synaptic even when I was first initiated into Ubuntu.

The name should definitely change, the different spelling variants of centre/center should automatically rule it out.

---

### Post by RAOF on 2009-05-28
> **jsmidt said:**
> Is DebTags already included into Ubuntu package management software?  If it is I didn't know about it.

Hm... I seem to remember playing with debtags & aptitude, but it seems that I'm thinking of the aptitude in Debian Experimental.

---

### Post by Slug71 on 2009-05-28
> **ranch hand said:**
> Slug71,
Don't get your knickers in too tight a knot, the world will not end for the lack of package kit.

As you can see from my sig, I am kind of interested in different OSs.  I had never really looked at Super OS (you refer to the old name).  I made the Ultimate Edition mistake and kind of turned me off to grandeous sounding Ubuntu varients.

I have to thank you for pointing it out again.

The gist of this is that I downloaded and installed the bugger.  I do not see any sign of packagekit.

It is a pretty nice OS from what I have seen of it.  I am on it now, exploring.

Meh, im over it. 

Yeh i think it is Autopackage that Super OS has by default. My bad.

---

### Post by gnomeuser on 2009-06-08
> **ranch hand said:**
> Slug71,
Don't get your knickers in too tight a knot, the world will not end for the lack of package kit..

Actually he is not the only one who is mighty upset. First of all PackageKit on brainstorm has been labeled as in progress for well over a year, giving the impression that we were getting PackageKit in some fashion.

PackageKit carries with it the promise of stronger integration, it gives us more granulated control over who can do what with package management. It gives application developers a toolset to have things installed on demand. 

If Ubuntu, one of the biggest distributions, after first signing on to that future, sudden dumps it for their own creation we are no further. The risks here are two fold, either Ubuntu gets sidelined and will ship without the features upstreams attach to integrate PackageKit or due to Ubuntu' decision not to support PackageKit upstreams will not integrate PackageKit out of fear that a large segment won't benefit and nobody will get a universal interface for managing software - an improvement which I suspect everyone can agree is a major advantage for Linux as a whole.

Instead of fixing dpkg to not do stupid things like stopping in the middle of a transaction to ask pointless questions (e.g. glibc is a wonderful example [x] want to upgrade libc? You call yourself debhelper? I just told you do to that earlier).  This isn't just a good idea to improve to fit better with PackageKit, it's a good idea in general as asking questions during a transaction is problematic at any rate, if need be asking them before a transaction is an option. 

Additionally these questions aren't translated (at least in any of the cases I have seen) which makes it a complete misnomer on the majority of the worlds desktops. 

Even if we absolutely needed these things present, surely one could patch PackageKit locally to support ones insanity, if something as complex as Gentoo' Portage can be supported sanely under PackageKits design I am sure dpkg can as well.

Instead they elect to use that problematic design which is fixable and will improve Ubuntu as a whole as the excuse for continuing fragmenting Linux in an area where we desperately need some standardization and rejecting an otherwise perfectly reasonable solution to a major problem.

Now they don't even give us a reasonable choice of installing PK ourselves as the repos contain a miserably old, unmaintained version, even in Karmic. This is just shining an even poorer light on PK to favor their own horrid all in one solution.

mpt might say I string people along, but he would be wrong, I did not initially label PackageKit as being in progress, I do not have a dictator of life chanting upstream upstream - and no PK is not just limited to Fedora just because it has it's origins there (no more than HAL, DeviceKit and many other things Ubuntu happily ships), it's true upstream: Pardus, Foresight, Fedora, Moblin, openSUSE (and probably more I don't have a full list in my head) all install and use packagekit by default to varying degrees. Gentoo is getting PackageKit support for Portage thanks to Google's Summer of Code this year. The list of supports grows every day and for good reasons. Even GNOME is reportedly considering some level of adoption of PackageKit in the future.

PackageKit is a widely accepted project that solves existing problems and gives us exciting new ways of using package management. Discarding it is damaging to Ubuntu and to Linux and does not fix actual problems in the status quo.

---

### Post by praveesh on 2009-06-08
Any idea about Ubuntu app centre ? Up to my knowledge , Ubuntu app centre is the code name of an application which is a combination of add or remove,synaptic,update manager , gdpkg(sorry I dont correctly remember the name). It is  scheduled to be included in karmic(up to my knowledge). One of the new feature is the  facility to buy paid application .

---

### Post by sim-value on 2009-06-08
Go to the Karmic forum :)

---

### Post by DeadSuperHero on 2009-06-08
If it's supposed to be modeled off of Apple's "App Store", I want nothing to do with it. I switched to Ubuntu because the software is free and easy, I don't want corporate garbage mucking up my system. 

If they implement it, might just be time to switch to Fedora.

---

### Post by sim-value on 2009-06-08
> **Mr. Psychopath said:**
> If it's supposed to be modeled off of Apple's "App Store", I want nothing to do with it. I switched to Ubuntu because the software is free and easy, I don't want corporate garbage mucking up my system. 

If they implement it, might just be time to switch to Fedora.

No its not ... 
[https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

---

### Post by aysiu on 2009-06-08
> **sim-value said:**
> Go to the Karmic forum :)
I've moved this thread there.

---

### Post by psyke83 on 2009-06-08
> **aysiu said:**
> I've moved this thread there.

Maybe it's better to close or merge this thread to avoid another [split]("http://ubuntuforums.org/showthread.php?t=1170534") discussion.

---

### Post by aysiu on 2009-06-08
> **psyke83 said:**
> Maybe it's better to close or merge this thread to avoid another [split]("http://ubuntuforums.org/showthread.php?t=1170534") discussion.
Good idea. Done.

---

### Post by ranch hand on 2009-06-08
> **jsmidt said:**
> Is DebTags already included into Ubuntu package management software?  If it is I didn't know about it.

"debtags" is available in synaptic (Jaunty anyway).

---

### Post by Swarms on 2009-06-08
> **Mr. Psychopath said:**
> If it's supposed to be modeled off of Apple's "App Store", I want nothing to do with it. I switched to Ubuntu because the software is free and easy, I don't want corporate garbage mucking up my system. 

If they implement it, might just be time to switch to Fedora.

If the software had a cost, but would save you hours of time, you would still not consider it?

---

### Post by Zorael on 2009-06-08
> **Swarms said:**
> If the software had a cost, but would save you hours of time, you would still not consider it?
To each his own; some are idealists, others are pragmatics.

---

### Post by Sand Lee on 2009-06-08
I side w/ **gnomeuser** and **Slug71** :popcorn:.

However, if AppCenter is inevitable, it should at least share package descriptions, or even better - use PK as its base instead of Add/Remove. If the latter isn't possible, PK should be able to coexist in Ubuntu for apps that have hooks for it.


The unrelated good news: GRUB2 is likely to be the default bootloader :P

---

### Post by caish5 on 2009-06-08
I think an appstore could be and easy and well integrated way for Ubuntu users to get acces to things that are currrently off limits to us.

Bluray playback, proprietary codecs etc.

Some things just have to be paid for in this world like it or not, with a store we have access, istead of just dual boot to windows.

---

### Post by Slug71 on 2009-06-08
> **gnomeuser said:**
> Actually he is not the only one who is mighty upset. First of all PackageKit on brainstorm has been labeled as in progress for well over a year, giving the impression that we were getting PackageKit in some fashion.

PackageKit carries with it the promise of stronger integration, it gives us more granulated control over who can do what with package management. It gives application developers a toolset to have things installed on demand. 

If Ubuntu, one of the biggest distributions, after first signing on to that future, sudden dumps it for their own creation we are no further. The risks here are two fold, either Ubuntu gets sidelined and will ship without the features upstreams attach to integrate PackageKit or due to Ubuntu' decision not to support PackageKit upstreams will not integrate PackageKit out of fear that a large segment won't benefit and nobody will get a universal interface for managing software - an improvement which I suspect everyone can agree is a major advantage for Linux as a whole.

Instead of fixing dpkg to not do stupid things like stopping in the middle of a transaction to ask pointless questions (e.g. glibc is a wonderful example [x] want to upgrade libc? You call yourself debhelper? I just told you do to that earlier).  This isn't just a good idea to improve to fit better with PackageKit, it's a good idea in general as asking questions during a transaction is problematic at any rate, if need be asking them before a transaction is an option. 

Additionally these questions aren't translated (at least in any of the cases I have seen) which makes it a complete misnomer on the majority of the worlds desktops. 

Even if we absolutely needed these things present, surely one could patch PackageKit locally to support ones insanity, if something as complex as Gentoo' Portage can be supported sanely under PackageKits design I am sure dpkg can as well.

Instead they elect to use that problematic design which is fixable and will improve Ubuntu as a whole as the excuse for continuing fragmenting Linux in an area where we desperately need some standardization and rejecting an otherwise perfectly reasonable solution to a major problem.

Now they don't even give us a reasonable choice of installing PK ourselves as the repos contain a miserably old, unmaintained version, even in Karmic. This is just shining an even poorer light on PK to favor their own horrid all in one solution.

mpt might say I string people along, but he would be wrong, I did not initially label PackageKit as being in progress, I do not have a dictator of life chanting upstream upstream - and no PK is not just limited to Fedora just because it has it's origins there (no more than HAL, DeviceKit and many other things Ubuntu happily ships), it's true upstream: Pardus, Foresight, Fedora, Moblin, openSUSE (and probably more I don't have a full list in my head) all install and use packagekit by default to varying degrees. Gentoo is getting PackageKit support for Portage thanks to Google's Summer of Code this year. The list of supports grows every day and for good reasons. Even GNOME is reportedly considering some level of adoption of PackageKit in the future.

PackageKit is a widely accepted project that solves existing problems and gives us exciting new ways of using package management. Discarding it is damaging to Ubuntu and to Linux and does not fix actual problems in the status quo.

Thank you Gnomeuser.

This is my biggest argument against AppCenter:

> If Ubuntu, one of the biggest distributions, after first signing on to that future, sudden dumps it for their own creation we are no further. The risks here are two fold, either Ubuntu gets sidelined and will ship without the features upstreams attach to integrate PackageKit or due to Ubuntu' decision not to support PackageKit upstreams will not integrate PackageKit out of fear that a large segment won't benefit and nobody will get a universal interface for managing software - an improvement which I suspect everyone can agree is a major advantage for Linux as a whole.

> Instead they elect to use that problematic design which is fixable and will improve Ubuntu as a whole as the excuse for continuing fragmenting Linux in an area where we desperately need some standardization and rejecting an otherwise perfectly reasonable solution to a major problem.

AppCenter already has a roadmap all the way to April 2011.
Imagine where Packagekit could be by that time.

I used 4.6 in Foresight and it is already a HUGE improvement over what is in Ubuntu's repos.

And we have an LTS coming up which is now going to have a half-a@#$ed package manager.

---

### Post by Slug71 on 2009-06-08
> **Sand Lee said:**
> I side w/ **gnomeuser** and **Slug71** :popcorn:.

However, if AppCenter is inevitable, it should at least share package descriptions, or even better - use PK as its base instead of Add/Remove. If the latter isn't possible, PK should be able to coexist in Ubuntu for apps that have hooks for it.


The unrelated good news: GRUB2 is likely to be the default bootloader :P

I do like the sound of Grub2 being default. :D

---

### Post by mpt on 2009-06-08
gnomeuser, good to see you haven’t given up on us yet.

> **gnomeuser said:**
> First of all PackageKit on brainstorm has been labeled as in progress for well over a year, giving the impression that we were getting PackageKit in some fashion.

In [the Brainstorm page you’re talking about]("http://brainstorm.ubuntu.com/idea/64/"), the specific ideas cited — “openoffice.org can use it for the installation [of] additional packages/art”, and “automatic printer driver download from lsb-site” — may indeed be implemented in Ubuntu using PackageKit. That does not mean Ubuntu needs to use PackageKit for anything else.

> *PackageKit carries with it the promise of stronger integration, it gives us more granulated control over who can do what with package management. It gives application developers a toolset to have things installed on demand.*

And it would facilitate us in leveraging actionable synergies across the middleware ecosystem too, I’ll bet.

> *If Ubuntu, one of the biggest distributions, after first signing on to that future, sudden dumps it for their own creation we are no further.*

“Sudden”? Have you been paying even the slightest attention to Ubuntu’s PackageKit discussions over the past two years?

> *Instead of fixing dpkg to not do stupid things like stopping in the middle of a transaction to ask pointless questions (e.g. glibc is a wonderful example [x] want to upgrade libc? You call yourself debhelper? I just told you do to that earlier).*

That would be a bug. It is the judgement of Ubuntu developers who are smarter than I am, that fixing that kind of bug by preventing any interaction at all would be throwing the baby out with the bathwater. If you want to change their minds, I suggest collecting more reproducible examples.

> *This isn't just a good idea to improve to fit better with PackageKit,*

That’s a fallacy, assuming the question.

> *it's a good idea in general as asking questions during a transaction is problematic at any rate, if need be asking them before a transaction is an option.*

That’s a good idea, thanks. I’ll investigate whether it’s possible, though I expect it isn’t (if some questions are based on things that the installation script discovers during installation).

> *Even if we absolutely needed these things present, surely one could patch PackageKit locally*

That is one option we are considering, though PackageKit’s redundant abstraction layer and primitive categorization system would also be drawbacks in using it to implement the user experience we want.

> *Instead they elect to use that problematic design which is fixable and will improve Ubuntu as a whole as the excuse for continuing fragmenting Linux in an area where we desperately need some standardization and rejecting an otherwise perfectly reasonable solution to a major problem.*

As far as I know, PackageKit has nothing particularly to do with Linux.

> *Now they don't even give us a reasonable choice of installing PK ourselves as the repos contain a miserably old, unmaintained version, even in Karmic. This is just shining an even poorer light on PK to favor their own horrid all in one solution.*

That’s only true if by “miserably old” you mean “only four months old”, and by “umaintained” you mean “maintained as the latest ABI-stable version”, and by “shining an even poorer light on PK to favor their own horrid all in one solution” you mean “I’m descending into unfounded conspiracy theories, someone please give me a hug”.

---

### Post by Reiger on 2009-06-08
> **gnomeuser said:**
> Even if we absolutely needed these things present, surely one could patch PackageKit locally to support ones insanity, if something as complex as Gentoo' Portage can be supported sanely under PackageKits design I am sure dpkg can as well.

Actually there already is such a thing: it is called KPackagekit. And to be frank the complete-package (package kit plus back ends) you get from Fedora Leonidas (yes I tried) was rather awful when I tried it: I could not get that package kit to do more than claim for 50 minutes that it was downloading a *single* package when it obviously was not. For some reason Leonidas had trouble properly recognizing my ATI card (which runs off the radeon driver in the xserver-xorg-video-ati package just fine in Ubuntu including having support for XRender compositing ...), which meant it fell back to 1024x768 resolution on a 1280x800 display. And would you know it: that package kit UI is utterly horrible at such a resolution.

And it *is* slow. I am sorry but if I compare the time wasted on the hassle of finding out what package I want through aptitude versus the time wasted on KPackagekit unfavourable speed at which it does anything at all (or at least the amount of additional time in which the application is unresponsive) I look favourably upon aptitude. In Leonidas Packagekit and its UI proved too slow to use: I had to resort to yum from the commandline to get anything installed at all.

In particular for such operations as "sudo apt-get update && sudo aptitude safe-upgrade" it is actually easier to type out that command on the commandline then to use the "Apply all available updates" in KPackagekit because of the time it requires to get that UI to show up.

But then again there is still a point that packagekit is where upstream development seems focused on, so one would expect heavy development and fixing of a lot of problems in such a crucial bit of software for a system that would use it as its default tool...

---

### Post by ghindo on 2009-06-09
> **mpt said:**
> gnomeuser, good to see you haven’t given up on us yet.:lolflag:

---

### Post by Nullack on 2009-06-09
gnomeuser is an insightful and helpful testing contributor to Ubuntu. It would be a great shame to see you head for other pastures my friend. He is a technically astute observer who's insights I respect. In a complex piece of software such as an operating system, there will always be differing views. The greatness of Ubuntu is the ability to express those openly, and potentially, impact change in a positive way.

---

### Post by ktp on 2009-06-09
> **mpt said:**
> In [the Brainstorm page you’re talking about]("http://brainstorm.ubuntu.com/idea/64/"), the specific ideas cited — “openoffice.org can use it for the installation [of] additional packages/art”, and “automatic printer driver download from lsb-site” — may indeed be implemented in Ubuntu using PackageKit. That does not mean Ubuntu needs to use PackageKit for anything else.

I hope you are kidding here...you might want to read the whole idea including the linked presentations to see what the idea was trying to say...not just the two simple examples given.

> **mpt said:**
> That’s a good idea, thanks. I’ll investigate whether it’s possible, though I expect it isn’t (if some questions are based on things that the installation script discovers during installation).

Couldn't the discovery be done before the transaction starts.  Simple example might help to understand the case you are talking about.

> **mpt said:**
> As far as I know, PackageKit has nothing particularly to do with Linux.

Wait what...nothing to with Linux...not even little.  I could be wrong but below quote makes it seem like something to do with Linux.

[QUOTE=http://packagekit.org/pk-intro.html]PackageKit is a system designed to make installing and updating software on your computer easier. The primary design goal is to unify all the software graphical tools used in different distributions, and use some of the latest technology like PolicyKit to make the process suck less. [/QUOTE]

---

### Post by mpt on 2009-06-13
> **ktp said:**
> Wait what...nothing to with Linux...not even little.  I could be wrong but below quote makes it seem like something to do with Linux.
[quote=http://packagekit.org/pk-intro.html]
PackageKit is a system designed to make installing and updating software on your computer easier. The primary design goal is to unify all the software graphical tools used in different distributions, and use some of the latest technology like PolicyKit to make the process suck less.
[/QUOTE]

That quote doesn’t even mention Linux.

Perhaps some examples will make this clearer. Android uses Linux, but I doubt it would make sense to use PackageKit on Android. The Palm Pre uses Linux, but I don’t think you’ll see PackageKit on the Pre any time soon. On the other hand, PackageKit probably would work on Debian GNU/kFreeBSD, which doesn’t use Linux at all.

---

### Post by ktp on 2009-06-13
> **mpt said:**
> That quote doesn’t even mention Linux.

Perhaps some examples will make this clearer. Android uses Linux, but I doubt it would make sense to use PackageKit on Android. The Palm Pre uses Linux, but I don’t think you’ll see PackageKit on the Pre any time soon. On the other hand, PackageKit probably would work on Debian GNU/kFreeBSD, which doesn’t use Linux at all.

good examples...I really like the examples you give...the once that help your arguments only.  But what about other distributions which do use Linux...Debian GNU/Linux, Suse, Fedora, ..., which can and in some case do use PackageKit by default.  Now since PK wants to "unify all the software graphical tools used in different distributions" and these, technically speaking, are Linux OS (that's what the OS tells me, even Ubuntu says its Linux), PK has something to do with Linux.

---

### Post by ranch hand on 2009-06-14
I had to play with Fedora again just to see if Package kit was as bad as I remember.

It is.  Compared to Mandriva (another RPM using system) you can get packages or updates in about four times the time.  It was so much fun that I just canceled and deleted Fedora again.  They really need a new package manager.

---

### Post by Slug71 on 2009-06-14
> **ranch hand said:**
> I had to play with Fedora again just to see if Package kit was as bad as I remember.

It is.  Compared to Mandriva (another RPM using system) you can get packages or updates in about four times the time.  It was so much fun that I just canceled and deleted Fedora again.  They really need a new package manager.

It seems Mandriva is also considering K/Packagekit to be default at the moment.

---

### Post by olskar on 2009-06-14
> **Slug71 said:**
> It seems Mandriva is also considering K/Packagekit to be default at the moment.

Poor Mandrivausers ;)

---

### Post by ktp on 2009-06-14
> **olskar said:**
> Poor Mandrivausers ;)

only time will tell.

---

### Post by psyke83 on 2009-06-14
> **ranch hand said:**
> I had to play with Fedora again just to see if Package kit was as bad as I remember.

It is.  Compared to Mandriva (another RPM using system) you can get packages or updates in about four times the time.  It was so much fun that I just canceled and deleted Fedora again.  They really need a new package manager.

I was unimpressed with the System Update function *at first* - it seemed to give no visual progress indication while the update was taking place. However, if you look at each individual update listed, the download progress is displayed for each item. The issue is that the "overall" progress is not informative, and in my case the mirror was quite slow. These factors could give an unfair impression of PackageKit, I think.

The updater only needs some slight interface tweaks (better overall progress indication, percentage text and estimated time remaining), but I still think that gnome-packagekit really sucks :P

---

### Post by ranch hand on 2009-06-14
> **olskar said:**
> Poor Mandrivausers ;)

Yes, I hare to hear they are even considering it.  Their system is much better as it is.

If that happens I do not see any non-.deb OSs that I really like and would recommend to folks except PCLOS-Gnome (uses synaptic).

---

### Post by ronacc on 2009-06-14
sometimes they are driven to fix what isn't broke :(

---

### Post by Mr. Picklesworth on 2009-06-14
I don't mind having a unique front-end, but I hope it can be communicated with via the PackageKit APIs.

Alas, PackageKit carrying the weight of a strict front-end is going to kill it. The only part I care about, and I don't think I'm alone, is having a standard way for applications to say "please install this" at runtime. The rest is entirely unimportant and not helpful.
Thankfully, it's dbus so anything could implement its interfaces.

In fact, I LOVE the sounds of this application. I hope it turns out as awesome and colourful as it sounds :)

---

### Post by mpt on 2009-06-21
In the PackageKit thread, Swarms asks:

> **Swarms said:**
> So how is Appcenter going? Can we compare the systems yet?

Not yet. :)

The first big challenge is finding the best overall metaphor to use for the interface. Because installing software on Ubuntu is so different from installing it on Windows or Mac OS X, we need to make our model as clear and understandable as possible. Our [Season of Usability]("http://season.openusability.org/") intern, Monica Maceli, is doing [preliminary research]("https://wiki.ubuntu.com/SummerOfUsability") on this, and I hope to start a public brainstorming session on that next week. Once that’s done we won’t need to use the AppCenter codename any more, because we’ll have found a good brand name to use.

Then we’ll mock up a dozen or so possible layouts for the main interface of version 4.0, before weeding them down to a few we can [paper-prototype]("http://www.alistapart.com/articles/paperprototyping") on potential users to see which one people understand the most. That way I can write up a design spec for version 1.0, in the knowledge that the design won’t need to change radically when features are added in later versions.

Meanwhile, there’s engineering work going on. [Michael Vogt]("https://launchpad.net/~mvo") has been researching what to use as a base — how easy it would be to make Add/Remove Applications work with PolicyKit, versus how easy it would be to hack the PackageKit infrastructure to support interactive installation, debtags, and keywords. We’ll discuss that tomorrow.

Separately, Michael has added a Keywords field to [the app-install-data-ubuntu package]("https://launchpad.net/ubuntu/+source/app-install-data-ubuntu"). This is a first step to making the search more useful to people who mis-hear or misspell an application name, or who are looking for an Ubuntu alternative to an application on another OS. So if you search for “Pigeon” you’ll get Pidgin as a result, if you search for “photoshop” you’ll get Gimp as a result, if you search for “worms” you’ll get Hedgewars as a result, and so on.

You heard all this here first!

---

### Post by 23meg on 2009-06-21
[QUOTE=mpt]Separately, Michael has added a Keywords field to the app-install-data-ubuntu package. This is a first step to making the search more useful to people who mis-hear or misspell an application name, or who are looking for an Ubuntu alternative to an application on another OS. So if you search for &#8220;Pigeon&#8221; you&#8217;ll get Pidgin as a result, if you search for &#8220;photoshop&#8221; you&#8217;ll get Gimp as a result, if you search for &#8220;worms&#8221; you&#8217;ll get Hedgewars as a result, and so on.[/QUOTE]

Is this using / going to use Debtags?

---

### Post by mpt on 2009-06-21
> **23meg said:**
> Is this using / going to use Debtags?

The Keywords field is not, no. Debtags are [a faceted classification]("http://debtags.alioth.debian.org/faceted.html") where each facet has a single value. Keywords, on the other hand, are arbitrarily long strings of keywords. They serve different purposes.

It’s quite likely that AppCenter will use existing debtags for other categorization purposes, though.

---

### Post by zekopeko on 2009-06-21
> **mpt said:**
> The Keywords field is not, no. Debtags are [a faceted classification]("http://debtags.alioth.debian.org/faceted.html") where each facet has a single value. Keywords, on the other hand, are arbitrarily long strings of keywords. They serve different purposes.

It’s quite likely that AppCenter will use existing debtags for other categorization purposes, though.

so if i got this right, debtags are gonna be used to show only GUI app to the end user and keywords are going to be used for end users ease of finding specific applications; ie image-editor,photoshop will lead to GIMP, right?

---

### Post by ranch hand on 2009-06-21
mpt and 23meg

This is off topic to a point but I think someone needs to take a moment and let you know that there are some of us out here that really thank you for what you are doing.

We also think that it is great that you particapate in the forums so that we can ask questionsand get answers from folks that actually have a clue as to what is going on.

Please ignore the hostilities of some of the folks that don't appear to have enough to do.

THANKS

---

### Post by ronacc on 2009-06-21
@ mpt  please announce the public brainstorming session so that those of us who are interested can join in .

some thoughts , trying to out windows windows or out mac apple will surely leave us in a position at best of always playing catchup . We do need to look at what they do right and do it better but in a unique way . we also need to look at what they do wrong and avoid their mistakes and irratations ( the constant reboots windows demands comes to mind , but thats easy for linux .)I find very little to dislike about our current package handeling so it will be interesting to see what others think .

---

### Post by ktp on 2009-06-21
> **mpt said:**
> In the PackageKit thread, Swarms asks:



Not yet. :)

The first big challenge is finding the best overall metaphor to use for the interface. Because installing software on Ubuntu is so different from installing it on Windows or Mac OS X, we need to make our model as clear and understandable as possible. Our [Season of Usability]("http://season.openusability.org/") intern, Monica Maceli, is doing [preliminary research]("https://wiki.ubuntu.com/SummerOfUsability") on this, and I hope to start a public brainstorming session on that next week. Once that’s done we won’t need to use the AppCenter codename any more, because we’ll have found a good brand name to use.

Then we’ll mock up a dozen or so possible layouts for the main interface of version 4.0, before weeding them down to a few we can [paper-prototype]("http://www.alistapart.com/articles/paperprototyping") on potential users to see which one people understand the most. That way I can write up a design spec for version 1.0, in the knowledge that the design won’t need to change radically when features are added in later versions.

Meanwhile, there’s engineering work going on. [Michael Vogt]("https://launchpad.net/~mvo") has been researching what to use as a base — how easy it would be to make Add/Remove Applications work with PolicyKit, versus how easy it would be to hack the PackageKit infrastructure to support interactive installation, debtags, and keywords. We’ll discuss that tomorrow.

Separately, Michael has added a Keywords field to [the app-install-data-ubuntu package]("https://launchpad.net/ubuntu/+source/app-install-data-ubuntu"). This is a first step to making the search more useful to people who mis-hear or misspell an application name, or who are looking for an Ubuntu alternative to an application on another OS. So if you search for “Pigeon” you’ll get Pidgin as a result, if you search for “photoshop” you’ll get Gimp as a result, if you search for “worms” you’ll get Hedgewars as a result, and so on.

You heard all this here first!

This is great...can you please let us know when the spec/prototype is posted.  Thanks for keeping the community in the loop, which can be hard at times because you can't make everyone happy, specially in the design.

---

### Post by ghindo on 2009-06-21
> **ranch hand said:**
> mpt and 23meg

This is off topic to a point but I think someone needs to take a moment and let you know that there are some of us out here that really thank you for what you are doing.

We also think that it is great that you particapate in the forums so that we can ask questionsand get answers from folks that actually have a clue as to what is going on.

Please ignore the hostilities of some of the folks that don't appear to have enough to do.

THANKS+1

Thanks for keeping the masses informed, guys :)

---

### Post by Starks on 2009-06-21
Stupid question...

Does AppCenter exist in bzr/source/deb form yet?

---

### Post by zekopeko on 2009-06-21
> **Starks said:**
> Stupid question...

Does AppCenter exist in bzr/source/deb form yet?

another <sigh> from me. did you even read what mpt posted? it's in the design phase, so no code to show for.

please read my post here:[http://ubuntuforums.org/showpost.php?p=7494754&postcount=83](http://ubuntuforums.org/showpost.php?p=7494754&postcount=83)

to understand why this is better. and do be patient. it's gonna pay of in the long run.

---

### Post by zekopeko on 2009-06-21
> **ronacc said:**
> @ mpt  please announce the public brainstorming session so that those of us who are interested can join in .

some thoughts , trying to out windows windows or out mac apple will surely leave us in a position at best of always playing catchup . We do need to look at what they do right and do it better but in a unique way . we also need to look at what they do wrong and avoid their mistakes and irratations ( the constant reboots windows demands comes to mind , but thats easy for linux .)I find very little to dislike about our current package handeling so it will be interesting to see what others think .

a couple of grievances from me:

all this "we must do it better, but in a unique way" is counter productive IMO. "we" don't need to do it in a unique fashion just to be unique. what "we" need to do is create a OS that users understand and love to use.
if we have to copy stuff from win or mac that's ok. and it doesn't have to be unique, just smarter or more consistent.

---

### Post by ronacc on 2009-06-21
> **zekopeko said:**
> a couple of grievances from me:

all this "we must do it better, but in a unique way" is counter productive IMO. "we" don't need to do it in a unique fashion just to be unique. what "we" need to do is create a OS that users understand and love to use.
if we have to copy stuff from win or mac that's ok. and it doesn't have to be unique, just smarter or more consistent.

what I ment by my above statement is that we should not slavisly duplicate another os's way of doing things .This is ofcourse only my opinion others may differ .as to the difference between doing it in a "unique way" and "just being unique" ,lets not argue phrasing  I'll accept your way of stating it .

---

### Post by zekopeko on 2009-06-21
> **ronacc said:**
> what I ment by my above statement is that we should not slavisly duplicate another os's way of doing things .This is ofcourse only my opinion others may differ .as to the difference between doing it in a "unique way" and "just being unique" ,lets not argue phrasing  I'll accept your way of stating it .

then i misunderstood you. i always here how Linux should be "unique" just for uniqueness sake. and that's not what i think Linux should do.

---

### Post by Swarms on 2009-06-22
Thank you for the update mpt, I am going to follow this project closely. :)

---

### Post by mpt on 2009-06-22
> **zekopeko said:**
> so if i got this right, debtags are gonna be used to show only GUI app to the end user

Add/Remove Applications currently distinguishes between graphical applications and everything else using the app-install-data-ubuntu package, not using debtags. I expect AppCenter will do the same.

> *and keywords are going to be used for end users ease of finding specific applications; ie image-editor,photoshop will lead to GIMP, right?*

“editor” and “photoshop”, yes, but gimp’s Keywords field wouldn’t need to include “image”, because [that word is already in the description]("https://edge.launchpad.net/ubuntu/karmic/i386/gimp/2.6.6-0ubuntu1").

> **ranch hand said:**
> THANKS

You’re welcome. :)

> **ronacc said:**
> @ mpt  please announce the public brainstorming session so that those of us who are interested can join in .

Will do.

> **ktp said:**
> This is great...can you please let us know when the spec/prototype is posted.

You can subscribe to [the wiki page]("https://wiki.ubuntu.com/AppCenter").

---

### Post by Slug71 on 2009-07-11
So has this started to come together yet, is there a PPA for it?
Theres little more than a month away until Feature Freeze. Surely they wont introduce this in a LTS release?

---

### Post by plun on 2009-07-11
> **Slug71 said:**
> So has this started to come together yet, is there a PPA for it?
Theres little more than a month away until Feature Freeze. Surely they wont introduce this in a LTS release?

Please read the wiki

[https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

;)

---

### Post by buzzmandt on 2009-07-11
I'm a bit late on this one but I'm happy to hear it, used kubuntus kpackagekit and really wasn't impressed with it compared to ubuntu's add/remove.

---

### Post by Regenweald on 2009-07-11
Scrunch Add remove and synaptic together, I'm good to go.

---

### Post by Slug71 on 2009-07-12
> **Regenweald said:**
> Scrunch Add remove and synaptic together, I'm good to go.

That would be Packagekit if it worked properly in Ubuntu. :P

---

### Post by Regenweald on 2009-07-12
> **Slug71 said:**
> That would be Packagekit if it worked properly in Ubuntu. :P

Indeed it would be :) but from the wiki app center looks ambitious and pretty damn cool for a central system. Once both PK and ApC mature, it'll all come down to our preference, which is great.

---

### Post by mpt on 2009-08-24
AppCenter now has an official name: the [Ubuntu Software Store]("https://wiki.ubuntu.com/SoftwareStore").

> **Slug71 said:**
> So has this started to come together yet, is there a PPA for it?

It’s currently in [one of Michael Vogt’s PPAs]("https://launchpad.net/~mvo/+archive/app-center").

> Theres little more than a month away until Feature Freeze. Surely they wont introduce this in a LTS release?

Ubuntu 9.10 will not be an LTS release.

---

### Post by meeples on 2009-08-24
> **mpt said:**
> AppCenter now has an official name: the [Ubuntu Software Store]("https://wiki.ubuntu.com/SoftwareStore").



It’s currently in [one of Michael Vogt’s PPAs]("https://launchpad.net/~mvo/+archive/app-center").



Ubuntu 9.10 will not be an LTS release.

gonna try it now :O

BIG NEWS.

---

### Post by taavikko on 2009-08-24
> **mpt said:**
> > Surely they wont introduce this in a LTS release?
Ubuntu 9.10 will not be an LTS release.

I think he/she meant that, appcenter shouldn't be introduced in 10.04 (LTS?)
But rather sooner (9.10), so it can be thoroughly tested :)

---

### Post by meeples on 2009-08-24
screenshot of Ubuntu Software Store (i'll still call it app center)


look at what i highlighted.

THERE GONNA START SELLING APPS?

---

### Post by taavikko on 2009-08-24
> **meeples said:**
> 
look at what i highlighted.

THERE GONNA START SELLING APPS?

They started that long time ago: [http://shop.canonical.com/index.php?cPath=19&osCsid=a3be105db24fec2373ef3e91b232aa5c](http://shop.canonical.com/index.php?cPath=19&osCsid=a3be105db24fec2373ef3e91b232aa5c)

now theyre just incorporating it to more convenient package.

---

### Post by ronacc on 2009-08-24
the ppa version looks good so far . I do see a few things that may need improving . 1 the "pending" that displays when an app is being installed should be changed to aomething like "in progress" , pending implies more action is needed to install it . 2 no indication when scrolling the list that an app is already installed , you have to click on the app to find that out , if I remember correctly in the preview that MPT linked to a while ago there was an indication in the list itself . 3 no detailed info on the apps for more advanced users ( dependencies , installed files , etc) possibly this is comming later? 5 since there are going to be both free ( as in beer ) apps and comercial (  $$$ ) apps there should be some "first glance" indication in the list as to which is which , without having to click on the app to find out . 

I do not list these things to imply that I do not like the progress being made , only to provide feedback .

---

### Post by jsmidt on 2009-08-27
HA!  The AppCenter is going to be an [App Store]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_software_store&num=1"). 

In fact, the new official name is now, pause for trumpets: [The Software Store]("https://wiki.ubuntu.com/SoftwareStore")!

Who would have guessed Canonical would be that forward about what the AppCenter actually is!

---

### Post by NCLI on 2009-08-27
Why shouldn't we be offering paid apps? Paid apps as an *alternative *to free apps can't possibly be a bad thing. Most of the best apps(The X server, Gnome, KDE, Firefox, OpenOffice) are backed financially by some kind of organization, which funds development and pays developers to work full time on the project.

And just look at what allowing paid apps has done for the iPhone, Android & the Palm Pre. Why shouldn't it help attract developers to Linux in the same way as it has done for these platforms?

---

### Post by Tibuda on 2009-08-27
Nothing wrong in selling software. This may bring some commercial software to Ubuntu/Linux.

Remember all the free-as-in-beer alternatives are still available.

---

### Post by psyke83 on 2009-08-27
> **danielrmt said:**
> Nothing wrong in selling software. This may bring some commercial software to Ubuntu/Linux.

Remember all the free-as-in-beer alternatives are still available.

Don't forget free-as-in-speech. Take the Medibuntu repository, for example. Components such as libdvdcss2 are open source, but restricted by potential patent/licensing issues. 

On the other hand, packages such as w32codecs are free-as-in-beer (or perhaps not, as some codecs may only be allowed to be distributed with Windows, even though they can be freely downloaded).

---

### Post by Merk42 on 2009-08-27
I wonder something about the store, though I don't know if this is the proper place to ask.

I live in the US, so legally I have to purchase the codec pack to play things like MP3s.

Say I do so, then I do a fresh installation (I have /home on a separate partition) is there any way of getting that codec pack back without repurchasing it?

---

### Post by steeleyuk on 2009-08-27
If you buy from Fluendo, you can just log back in using your account on the Fluendo website and download the latest deb. Thats what I do with the DVD Player anyway...

---

### Post by Merk42 on 2009-08-27
> **steeleyuk said:**
> If you buy from Fluendo, you can just log back in using your account on the Fluendo website and download the latest deb. Thats what I do with the DVD Player anyway...

I see I wonder if the Software Store will have a thing like that.  Like STEAM.
Oh even better would be if it kept track of what you had installed, then after a fresh installation, you could just sign it and it'd re-install everything.

---

### Post by Bios Element on 2009-08-27
> **Merk42 said:**
> I see I wonder if the Software Store will have a thing like that.  Like STEAM.
Oh even better would be if it kept track of what you had installed, then after a fresh installation, you could just sign it and it'd re-install everything.

If it doesn't then you can count on someone adding that. An iPhone-style "App Store" for the desktop is frankly an amazing idea that could have a massive future.

---

### Post by NCLI on 2009-08-27
> **Merk42 said:**
> I see I wonder if the Software Store will have a thing like that.  Like STEAM.
Oh even better would be if it kept track of what you had installed, then after a fresh installation, you could just sign it and it'd re-install everything.
I think it will use your OpenID.

---

### Post by jsmidt on 2009-08-27
I never said I was against an App Store.  In a previous thread I said I hope to have it.

I just wanted to point out this is probably the real reason Canonical is putting so much effort into this thing.  It's just a reality of life: effort goes to what brings you money, regardless how you spin it.

*If all the App Center/Store would do is make the community happy, Canonical wouldn't do it*! 

This isn't a bad thing!  But this is further evidence that what is really behind all of Canonical decisions, as all other commercial entities, is making money. 

However, Canonical welcomes all free contributions from the community, :) so it's a good for them some people are motivated by things other than money.


*BUT LET ME REPEAT*: I am all for what Ubuntu is becoming; a polished distro that is the perfect mix of commercialism plus free labor Canonical extracts from a community.  

If Canonical can gain more money from this same community through their App Store, good for them! :)

---

### Post by jsmidt on 2009-08-27
By the way, Ubuntu is further proof that all good things take money, and a very efficient business man who knows how to get the most out of that money. (You can't beat free contributions!)

Can someone name something good that didn't take a leader driven by money?

---

### Post by 23meg on 2009-08-27
[QUOTE=jsmidt]Can someone name something good that didn't take a leader driven by money?[/QUOTE]

I'd rather we kept on topic.

---

