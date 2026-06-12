---
title: "How does a new user troubleshoot anything?"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Yashiro on 2009-02-27
When there is no application like Hardinfo, or similar, installed by default?

Even the simple task of of finding out which video driver is running is not easy for someone not familiar with Linux.

---

### Post by Nullack on 2009-02-27
See the contributing to Jaunty thread, especially the debugging guides.

---

### Post by Yashiro on 2009-02-27
The point being a new user cannot find out simple machine specific information. I am not asking for help for myself here, I'm highlighting a flaw that exists for the non technical end user.

If the answer is 'put these commands into a terminal' then there is a failing to expose information. 
Not everyone is technically adept. Requiring the less nerdy folk to use the terminal will not do ubuntu any favours in the long term.

---

### Post by Nullack on 2009-02-27
Theres a gnome gui hardware utility, cant rmember name, might have been hardinfo or something.

---

### Post by taavikko on 2009-02-27
"sysinfo" is one utility

---

### Post by ronacc on 2009-02-27
troubleshooting anything is difficult for those unfamiliar with what they are trying to fix , not just linux .For those unwilling to educate themselves no reasonable amount of automation is likely to be much help .The ready availability of a fully functional and powerful terminal is one of the strengths of linux not one of the weakneses .Including hardinfo or sysinfo by default would be a good idea but would the newbe know to use them or how to interpet the information they are giving ? With that said , the forums are the best source of help when things go wrong , however if the newbe is unwilling to put forth any effort to help themselves I doubt that they can be helped .

---

### Post by taavikko on 2009-02-27
@ronacc +1

Every new thing needs some self learning, even a freakin toaster.
If you're not willing to spend some time learning, why should that be reason enough to dumb down linux?

---

### Post by cecilpierce on 2009-02-27
Linux for Dummies is a good book for beginners and you can read it on line.

---

### Post by MaX on 2009-02-27
in Windows (98, XP, Vista) there has been a program for some time now called DxDiag (Direct X Diagnostic Tool) that does what we wan't.

(I've attatched the output from my computer (I had to cut some directshow filters because of the size limit on attatchments).

It basically looks like this:```
------------------
System Information
------------------
Time of this report: 2/27/2009, 13:41:50
       Machine name: LILLEMOR
   Operating System: Windows Vista™ Ultimate (6.0, Build 6001) Service Pack 1 (6001.vistasp1_gdr.080917-1612)
           Language: Swedish (Regional Setting: Swedish)
System Manufacturer: System manufacturer
       System Model: System Product Name
               BIOS: Phoenix - Award BIOS v6.00PG
          Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2 CPUs), ~2.2GHz
             Memory: 2046MB RAM
          Page File: 1080MB used, 3253MB available
        Windows Dir: D:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6001.18000 32bit Unicode

```

---

### Post by Sockerdrickan on 2009-02-27
[apt://hardinfo](apt://hardinfo) generate report

---

### Post by MaX on 2009-03-01
> **Tux0r said:**
> [apt://hardinfo](apt://hardinfo) generate report
Did you read the first post?
What if hardinfo is not installed?

Maybe it should be from the beginning?

---

### Post by Gina on 2009-03-01
A new user would be best advised to start off with a fully released working version of Ubuntu eg. 8.10.  At least then if things go wrong there is less chance of it being due to a bug in the operating system.  Get used to how things work and give it a good workout while you learn the new system.  And yes, books and foruns are a great source of info and help.  I don't feel it's very sensible to make things knowingly more difficult by using experimental software.

---

### Post by scaine on 2009-03-01
Well, true - don't use alphas if you're just starting out.  But I think it's a good point.  There used to be a device manager type app in system/admin, but it's long gone as far as I can tell.

You know the only thing I miss from my Windows days?  Well, apart from being able to play the latest games of course?  The device manager.  It was a deceptively powerful tool that provided an immense amount of information that you might never need to know, but it provided that information elegantly and with the power to do something about it if there was something wrong.

Didn't always help, of course, but it was usually a starting point.  I've just spent a moment or two there and I think that that really is the only thing I miss from Windows.  Oh!  And being able to specify a speed for my ethernet card!  Ethtool is fine, I suppose, but if they integrated that into Network Manager, it would be better.

On Ubuntu, your only recourse for hardware, either in your system, or about something you've just plugged in, is to open a terminal and type dmesg, then hope to hell you understand what all that means, or post it on here and hope to hell someone cares enough and knows enough to help.

Right, I'm off to install sysinfo and hardinfo to see what they're all about.

[EDIT] Hardinfo is really nice!  Live graphs and everything!  I'm less impressed by Sysinfo - can anyone who knows tell me if there's any reason to install sysinfo over hardinfo?  On first impressions, Hardinfo certainly seems like the more polished software.

---

### Post by nyarnon on 2009-03-01
> **MaX said:**
> in Windows (98, XP, Vista) there has been a program for some time now called DxDiag (Direct X Diagnostic Tool) that does what we wan't.




How do you mean, thats just a support program for the directX layer. Anyway hardware info under linux can easily be obtained by lshw lsmod lsusb lspci. But as already mentioned in this thread without efford no one will ever know about it not even about dxdiag.

---

### Post by nyarnon on 2009-03-01
> **MaX said:**
> Did you read the first post?
What if hardinfo is not installed?

Maybe it should be from the beginning?

lshw is BE from the beginning. Simple. :guitar:

---

### Post by sgosnell on 2009-03-01
I've never seen a Windows newbie who even knew about Device Manager, much less how to get to it.  Most Windows users have no clue about what system they have or how it works, other than it's Vista, XP, or something.  They struggle with software installation, and really struggle with any computer administration.  Windows is no easier than Linux in this area - both require some effort and experience.

---

### Post by ronacc on 2009-03-01
one big difference is that there are about a zillion shops that will be very happy to straighten out their windows box for $$$ .

---

### Post by nyarnon on 2009-03-01
> **ronacc said:**
> one big difference is that there are about a zillion shops that will be very happy to straighten out their windows box for $$$ .

Guess what, I make a living on it. And guess again. Where ever I can I port my clients to Ubuntu. Except for me nothing really changes, I still earn my support fee but instead of solving problems with inferior software I now start educating.  My customers develop skills they couldn't under windows and they finally get a day work done on there boxes. So be carefull what you say about a 'zillion shops' I'm one of them.

---

### Post by WatchingThePain on 2009-03-01
Welcome to Linux.

---

### Post by ronacc on 2009-03-01
> **nyarnon said:**
> Guess what, I make a living on it. And guess again. Where ever I can I port my clients to Ubuntu. Except for me nothing really changes, I still earn my support fee but instead of solving problems with inferior software I now start educating.  My customers develop skills they couldn't under windows and they finally get a day work done on there boxes. So be carefull what you say about a 'zillion shops' I'm one of them.

I was by no means saying anything bad about those shops , they fill a need and that is a legimate buisnees model , in fact it is the very basis of capitalism to see a need and fill it and thereby earn a profit . I am happy that you try to switch people to linux and to educate them , I wish shops in my area did that .The usual response I get when I say I run linux is either huh? or "why don't you run windows" .

---

### Post by Sockerdrickan on 2009-03-01
> **WatchingThePain said:**
> Welcome to Linux.
I wish the thanks button was still there. :lolflag:

---

### Post by autocrosser on 2009-03-01
The thing I see here is that by the time someone really needs sysinfo or hardinfo--they know how to install it---same thing about lshw--the person knows how to use it--the point being that novices that use alpha software very easily get in way over their head......I have FAR too often seen a novice that after thinking that the new release would be "cool" to use---come & cry here that their system is broken & demands that we need to help fix the problem "AT ONCE!!!"


The sticky at the top of the forum is targeted at those people--I for one, watch my system, make informed responses to software upgrades & promptly report bugs..I've been doing this for 4 years now with Ubuntu & 10 years with Mac OS before that......I've posted in another thread---It's like looking at a old map---the verges state "beyond here be Dragons"--We are always sailing into uncharted waters with every update we do....most are safe, but every once in a while you get bit :lolflag:

---

### Post by Nullack on 2009-03-02
Exactly autocrosser - besdies, where do you hide the complexity anyway. Computer science isnt trivial, these are complex machines.

---

### Post by nyarnon on 2009-03-02
> **ronacc said:**
> I was by no means saying anything bad about those shops , they fill a need and that is a legitimate business model , in fact it is the very basis of capitalism to see a need and fill it and thereby earn a profit . I am happy that you try to switch people to linux and to educate them , I wish shops in my area did that .The usual response I get when I say I run linux is either huh? or "why don't you run windows" .

Black sheep indeed. I notice, hence I got work and they don't. Especially considering the crisis I notice people with XBOX experience opening up shops as fast as closing them. IMHO it's impossible to have/maintain such a shop as you can impossible keep a stock. Hence 20 years ago I went completely into service. Now I get paid by a fixed hourly fee. 

I'm happy, my customers know what they pay for and I'm in the lucky position to advise them untainted on any hardware/software without caring of my stock thats picking up dust. And if they need anything I pick it up for them at the cheapest location hand them the receipt and collect the same hourly fee.

Now as you can see with this model I save myself and my customers a lot of headache. I can create a trusted environment where customers are quicker to take advise. And under this model I can safely say, steer free of any support shop that maintains a hardware stock. They can only survive if they steal.

It also at the same time propagates the use of open software, the philosophy is easy. Any dime I save a customer is a dime (s)he can spend on me. So no need to sell them proprietary software if there is a free alternative. The need of the customer comes first. I do not earn more or less by advising either OOO or MSO.

So feel free and let any of these 'shops' read this message. Maybe some of them are intelligent enough to comprehend and start considering replacing their model for mine. The quality should raise automagically.

---

### Post by Nullack on 2009-03-02
In enterprises as servers, HPC or network components, Linux and *nix like OS's are pretty common. Many of them run headless or as hosts for VMs and there is a minimalist philosophy with configuration.

Desktop linux isnt so common. Why? Because some key desktop architecture elements are not complete and have more bugs than MS Windows Desktops or Max OS X. Its exciting to see that these things are being worked in the FOSS ecosystem but its a misrepresentation to think that FOSS Desktops currently match leading commercial ones.

I like being involved in the systems development that Ubuntu offers, which is why I use it on my systems.

---

### Post by nyarnon on 2009-03-02
> **Nullack said:**
>  Because some key desktop architecture elements are not complete and have more bugs than MS Windows Desktops or Max OS X.

Please elaborate. What do you call not complete? And what would have more bugs? Obviously it is stable enough for some hardware houses to put it on their desktops. The only thing hampering the exodus from MS being IMHO the used business models. It's creeping them out not to have a stick to hit somebody if anything goes wrong :-) But MSes abuse and mistreatment of partners ( especially under Vista) did make'm reconsider :-)

---

### Post by ronacc on 2009-03-02
@ nyarnon  I too have a small service buisness ( nothing to do with computers) and exactly the same buisness model , Treat the customer fairly and honestly . I am tied to no particular "brand name" and thus can advise my customers without regard to my "bottom line" and also save myself $$$ by not having to maintain a "floor stock" . The result is that I have a fiercely loyal customer base in a buisness where most shops are hated ,and more work than I really want since the stuff I work on requires routine service as well as repairs .

---

### Post by nyarnon on 2009-03-02
> **ronacc said:**
> The result is that I have a fiercely loyal customer base .

Which also saves you advertising costs doesn't it. Now who is going to take this to banks and goverments? :-)

---

### Post by ronacc on 2009-03-02
my advertiseing costs are 0 , my customers do it for me :P

---

### Post by Nullack on 2009-03-02
> **nyarnon said:**
> Please elaborate. What do you call not complete?:-)

Things such as:

* A glitch free audio stack, that is sufficiently robust across the entire audio stack
* Working universal GPU memory management in the kernel.
* Related video drivers to support this in the kernel. Finally fixing compiz and other related areas from the currently broken architecture.
* Across the board implementation of GPU acceleration for video decoding on GPUs that support it
* Gstreamer based DVD and Bluray software for demuxers, decoders and navigators
* Mono to catchup for the newer versions of .Net and for the performance problems to be resolved (since we allready have good java support with Sun's binaries or OpenJDK)

I'm pleased to say that work is coming along with these gaps. In particular the VDPAU acceleration, while buggy right now, is an excellent showcase of the benefits for multimedia - my low end AMD Sempron with an old 8600 GT card which I use for testing is capable of decoding full 1920x1080 VC-1 and AVC streams (high profile included) with very little CPU utilisation. Fixing up the whole audio and video stacks in linux and being relentless with achieving robustness in these areas is really a key step I cant wait to see happen.

Understandably, desktops are commonly asked to do allot more things than a server so Im not suprised that the FOSS desktop experience lags behind the competitiveness of the server experience.

---

### Post by nyarnon on 2009-03-02
O common Nullack, that's hardly fair is it. Just because some new stuff is developed first for windows cannot mean that you can dismiss the Linux desktop as not complete. In fact the best multimedia boxes are based on Linux. 

Anyway once MS rein is over (and Europe is trying hard to establish that) things will quickly change. Not in the sense that Linux is becoming better but in the sense that more and more hardware manufacturers start standardising and producing open drivers.

Nice example is that Europe is on the brink to make phone makers adapt a universal adapter to load cellphones. And more is coming.

---

### Post by ronacc on 2009-03-02
With the usual disclaimer that it is alpha software , I installed windows7 just to see what the fuss was about , I was not impressed , it couldn't even get the refresh rate correct on my very common samsung WS lcd and of course refused to allow me to set it correctly, giving a ( while quite beautiful ) flickering display that would quickly result in headaches . this build (7022) had IE8 , hohum .It also bitched because I wouldn't let it call home and report the particulars of my box to MS so they could "keep tabs" on me.

---

### Post by Nullack on 2009-03-02
@ nyarnon, I use Linux for HTPC and multimedia, so I know its capabilities well. :)

OSX and XP/Vista/Win7 have gpu memory management, gpu video acceleration, a complete compositing solution and a robust audio stack. The fact is that Linux suffers badly in these areas with buggy and incomplete capabilities. This causes serious problems, such as how VDPAU artifacts badly under gpu accelerated AVC. Goodluck playing back high profile AVC content with post processing filters without GPU acceleration :)

To say that Linux somehow offers the best multimedia experience is to totally ignore the capabilities of OSX and Windows. Put simply, it has useful features that Linux doesnt have. Hopefully the FOSS ecosystem will sort this out, but then again, its been years that robust gstreamer dvd navigation has been supposedly coming. Maybe it will take more time than whats apparent.

@Ronacc - 

I quite like the idea of how MS are using the beta telemetry of systems to gather real world metrics on performance, crashes and so on. Really I think the FOSS world should use more of this - say not just doing apport crashes like now or kernel oopses reporting, but also doing performance stuff as well. Say, a special alpha release could be issued, then a special beta release, with performance monitoring turned on that reports back to Canonical so they can get allot of real world data.

If you feel your privacy is being violated by MS I suggest you check out their privacy policy - AFAIK in America there is law on those sorts of issues.

---

### Post by ronacc on 2009-03-02
I have no wish to launch into a troll on the perfidity of MS since I have not "used" any version of windows for 10 years . I merely wanted to indicate that they are not "perfect" either .

---

### Post by Nullack on 2009-03-02
Ofcourse they arent :) No harm though in learning from the good things they do, like how they proved prefetch has peformance benefits on typical desktop systems.

---

### Post by nyarnon on 2009-03-02
@ Nullack

Your specialised requirements are in no way proof of that the Linux desktops would not be complete. Especially considering that it is free and open. I'm serving a wide client base as where the Linux desktop is concerned and I yet have to find an ms app that cannot somehow be replaced.

As for the hardware as long as the industry doesn't comply to their own standards how can you expect a user base to develop working adaptations?

---

### Post by Nullack on 2009-03-02
> **nyarnon said:**
> @ Nullack

Your specialised requirements are in no way proof of that the Linux desktops would not be complete.

Mate I think that its a fair point that HD playback could be considered specialised. However I do consider common things to be broken:

* DVD playback to be pretty common and this is broken. Mplayers implementation is far better than resindvd for gstreamer, but it is also bugged in certain areas. It doesnt just work(TM).

* The Linux Audio stack is broken. The architectural move to glitch free audio playback was the right one, which OSX and Windows allready have, but its plagued by bugs currently. Look around the blogsphere for comments on pulse bugs.

* Compiz is broken (which Ubuntu enables by default with supporting drivers). Until there is kernel based gpu memory management and full driver support, things like compiz wont every work in a robust manner. Again, have a look around the blogsphere on the details for this breakage.

---

### Post by oldsoundguy on 2009-03-02
The media reasons above are one of three reasons I still maintain a Windows XP box (actually two)(but a Windows update borked my digital output on the Creative X-Fi and there has been no answer to eMails sent out over a MONTH ago .. analog works fine).  
Another is Adobe and my photography .. after tying up all of those bucks in software, I am not going to toss it!  And not ALL (actually not much) of Adobe works in Wine or any other add on, paid for or not. 
Then there are  the  instructional DVD's .. for some reason (think it has to do with Quick Time in most cases) they just do not function properly on any of my Linux boxes.

The original troubleshooting question partially boils down to finding out what REALLY is in that box .. there are the lshw and related commands that you can run in terminal. save to Tomboy or such (cut and paste) (or send to your printer with another command) and print out .. that will give you a really good idea of what you have to work with.  
But think one of the OPs was looking for a silver bullet program such as Sandra or Belarc to do the do and print from all in one fell swoop.  Does not exist as of NOW as far as I have heard.

---

### Post by nyarnon on 2009-03-03
Well here I'm lost as on ALL of my machines DVD playback works just fine in VLC aswell as Totem and for the handywork (ripping/editing/transforming) MPlayer.

As for Adobe and money tied up, that's of course exactly what they want. I'm quite happy with Gimp, Imagemagic, Picasa and last but not least NetPbm.

Of my 5 boxes at home two have HDAudio, both work fine right of of the box. The Jaunty one has the current dev problems but thats to be expected on a dev platform.

As for compiz I can only state that it works as expected even on my tiny atom based and intel graphics running eeepc 1000h. Yes even the rotating cube and beryl work fine without any crashes.

To finish this answer I would like to point to MYTH, probably currently the best project to demonstrate that multimedia on Linux works on a professional level. Many commercial multimedia hardware projects are based on Myth and people make a living off it.

As for dvd problems they usually occur if the right drivers are missing. But given that you are pro's I do expect that you have ubuntu-restricted and other drivers installed. So my guess is that your problems occur from exotic hardware and if that so the only one to solve your problems is most probably the producer of your hardware.

But as you said yourself  getting help on a commercial level is hardly compared to that of a loving and caring community like Ubuntu.:lolflag:

---

### Post by Yashiro on 2009-03-03
I wasn't looking for anything. I was questioning how it was intended to be done. 

Telling users to get straight into the terminal to find out if their hardware is recognized and what video driver is in use is wrong for an end user desktop and should be addressed.

I know full well about all the varied utilities. I've used Linux for years, but my Mum and my friends have not.

The utility provided on the OpenSolaris desktop or something like a working/updated Hardinfo is needed to be installed by default.

---

### Post by nyarnon on 2009-03-03
[QUOTE=Yashiro;6829040
Telling users to get straight into the terminal to find out if their hardware is recognized and what video driver is in use is wrong for an end user desktop and should be addressed.[/QUOTE]

XDIAG? nuff said.

Sure it has a window but it's hardly easier to find/reach then lshw and most of the time I run Ubuntu live cd's to get my customers specs with the ls* family and store them in my customer base for later refferal.

---

### Post by lean on 2009-03-03
> **nyarnon said:**
> Well here I'm lost as on ALL of my machines DVD playback works just fine in VLC aswell as Totem and for the handywork (ripping/editing/transforming) MPlayer.


I guess it is has been a year or so since you _bought_ a DVD? A lot of new DVD's have RipGuard or ARccOS protection, and none of these can be played (or ripped) in Linux.

---

### Post by nyarnon on 2009-03-03
> **lean said:**
> I guess it is has been a year or so since you _bought_ a DVD? A lot of new DVD's have RipGuard or ARccOS protection, and none of these can be played (or ripped) in Linux.

No the last one I bought is a cheap external eSAU208 from Lite-on a few weeks ago and it works just fine. But your remark illustrates again how manufacturers frustrate and not the desktop. Be careful what you buy. And don't blame your garage if it can't repair your car because propitiatory tools are needed.

O you mean the DVD itself? Same applies. You cannot state a desktop as incomplete because people try to protect their work. Just bring back the DVD and ask your money back or go to the PirateBay and get a playable copy. It illustrates their legit :-)

---

### Post by ronacc on 2009-03-03
> **Yashiro said:**
> I wasn't looking for anything. I was questioning how it was intended to be done. 

Telling users to get straight into the terminal to find out if their hardware is recognized and what video driver is in use is wrong for an end user desktop and should be addressed.

I know full well about all the varied utilities. I've used Linux for years, but my Mum and my friends have not.

The utility provided on the OpenSolaris desktop or something like a working/updated Hardinfo is needed to be installed by default.

Why doesn't the newbe know how to use the terminal ? Ignorance , I do not mean that in a derogatory way , it is the natural state when one is dealing with something new . What is the cure for ignorance ? education .We who have have been around a while have learned , share that knowledge . Give a man a fish and you feed him for a day , teach a man to fish and you feed him for life . I do not mean that no attempt should be made to simplify things where it makes sense to do so but to raise up a vast and rickety structure to handle something that a little education would easily accomplish rarely makes sense and often fails . There always seems to arise in threads of this type 2 philosophies , one which says we must hide away all knowledge and keep it only for the "initiated" and one which says educate . Is there any doubt which side I stand on .

---

### Post by Nullack on 2009-03-03
> **nyarnon said:**
> Well here I'm lost as on ALL of my machines DVD playback works just fine in VLC aswell as Totem and for the handywork (ripping/editing/transforming) MPlayer.

Hi nyarnon;

Ubuntu uses gstreamer by default, lets look at what the dev documentation says about resindvd:

"Stream Selection - Status thaytan has some local changes to send an event downstream from rsndvdsrc and handle it in rsnstreamselector so that the subpicture and audio tracks can change when commanded to by DVD menu operations. It needs more work.

Player UI integration - Status Not started

Switching Audio Decoder Bin - Status Not started

Audio Munger - Status In progress

Seeking - Status Time based seeking partially implemented - works for PGC's with a time-seek table, which is usually only the main movie.

Multi-angle - Status Not started.

Playbin2 Integration - Status Not started 

Alternate display modes - Status Not started.

* Make DURATION reporting in rsndvdsrc synchronised with the display, to avoid wackiness.

* Shorten playbin queues in 'DVD mode'. There's no need to have 3 seconds of output buffers in playbin for ResinDVD

There are probably still other things that need implementing, and plenty of bugs to fix."

Aoart from all the problems with gstreamer, mplayer and VLC have gotten further along the path to robustness with dvdnav. However, its also not complete and has numerous bugs. For example, using dvdnav with mouse movements the audio stream selection and subtitle selection functionality all fails to work and the alpha image highlight selection code is incomplete.

> **nyarnon said:**
> As for compiz I can only state that it works as expected even on my tiny atom based and intel graphics running eeepc 1000h. Yes even the rotating cube and beryl work fine without any crashes.

This second post summarises why the architecture is broken for composting:

[http://www.phoronix.com/forums/showthread.php?t=7889](http://www.phoronix.com/forums/showthread.php?t=7889)

With pulseaudio, Im sure you can find many internet examples of all the problems Linux is having with implementing glitch free audio playback.

As I said, Linux is a good viable solution for servers and the like, but for the added requirements of a desktop OS it is by no means a feature by feature alternative to what OSX and Windows offers. Hopefully that will change into the future :)

---

