---
title: "Never ending installation"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by afrocod on 2011-07-25
I've never installed Ubuntu on any machine before and I'm a bit of a novice. So I'm installing it on an old Toshiba laptop that was running XP. It wouldn't automatically boot from CD so I held F12 and selected the boot from CD option and the next screen is all black with 

[ 0.124007]  [<c1..........>] ? ..........................

[ 0.124007]  [<c1..........>] ? ..........................

[ 0.124007]  [<c1..........>] ? ..........................

[ 0.124007]  [<c1..........>] ? ..........................

covering the entire screen  where the left column of dots are number changing very fast and the right column is word commands like show_trace 000x452 (It's changing very fast and I cant really see what it say's, it's just to give you an idea)

It's been like this for about half an hour so I'm assuming nothing is really happening but then again I really haven't a clue.

EDIT: I just took a picture. It's probably a lot clearer than this explanation

[IMG]http://www.giantbomb.com/profile/afrocod/all-images/52-399595/img_2500/51-1847065/[/IMG]_[IMG]http://www.flickr.com/photos/65633479@N03/5975012781/[/IMG]_[[IMG]http://farm7.static.flickr.com/6139/5975012781_5f9440d18d.jpg[/IMG]]("http://www.flickr.com/photos/65633479@N03/5975012781/")
[IMG_2500]("http://www.flickr.com/photos/65633479@N03/5975012781/") by [C.P. O'Donnell]("http://www.flickr.com/people/65633479@N03/"), on Flickr

Any help would be much appreciated.

Thanks in advance 

Cillian

---

### Post by 3602 on 2011-07-25
Do these texts stop here (in your photo) or do they keep rolling on and on?
I see two possibilities...
One. The video system on your computer is incorrect. Generally you don't see this stuff. It's in the background "covered" by a purple screen with orange dots rolling on it.
Two. The disk or the ISO file is corrupt. Try burning at the slowest speed possible and, if that doesn't solve it, try re-downloading the ISO file.
Alternatively, to check whether this is an isolated case, try downloading another distro and see whether you get some graphics instead of this.

---

### Post by afrocod on 2011-07-25
They keep rolling on and on. I can't even read them, the camera was just quick enough to catch it.
 
I'm unsure how to check or fix you first scenario but I will go try and burn the iso at the slowest speed and see what happens.

I'm also unfamiliar with the term distro. Could you explain?

> **3602 said:**
> Do these texts stop here (in your photo) or do they keep rolling on and on?
I see two possibilities...
One. The video system on your computer is incorrect. Generally you don't see this stuff. It's in the background "covered" by a purple screen with orange dots rolling on it.
Two. The disk or the ISO file is corrupt. Try burning at the slowest speed possible and, if that doesn't solve it, try re-downloading the ISO file.
Alternatively, to check whether this is an isolated case, try downloading another distro and see whether you get some graphics instead of this.

---

### Post by afrocod on 2011-07-25
@3602 So I burned it at the slowest speed on a different laptop just in case and it's the same old story the only difference is the 0.124007 has changed to 0.120006 (I'm not sure what is useless information and what is not so I'm just trying to list everything).

Also when I insert the CD when XP has already booted and on the desktop it starts just fine with the proper Ubuntu graphical interface appearing and telling me I need to reboot and install. Also I've checked the contents and all the folders and files are present so I assume that means it is not corrupted.

Thanks for the response by the way, I thought the post was going to slip away into the abyss there for a second.

---

### Post by 3602 on 2011-07-25
OK. If you insert the CD *with XP running*, you *might* be booting Wubi and other bad news.
Other than that, distros. Try [Fedora]("http://fedoraproject.org/"). If you have many blank disks lying around... Since you're running on CDs you can't try Suse, that needs a 4.7GB DVD. Try [Mandriva]("http://www.mandriva.com/en/downloads/one/") too. If one of these distros can boot into beautiful graphics, then... I'm not sure. If none of these would boot into graphics then I'm not sure either...
I see you have Toshi there. They have the worst Linux support (apparently) but should *not* have *this* problem. What is your graphics card/chipset?

---

### Post by Miljet on 2011-07-26
You did burn the ISO as an image to the disk didn't you? And not just copy the file?

---

### Post by afrocod on 2011-07-26
@Miljet Yes I definitely burned it and not just copied the files. I'm 100% sure of that.

@3602 Sorry we live in different timezones. I'm just up now, so I'll go check those distros and see what happens

As for graphics card, chipset. Well if that was going to be a problem, then I bet that's the problem. It's a terribly old laptop that I was just going to throw away. Intel pentium 4 and some very old ATI graphics card which I can't find the spec's for. I was going to give it a new lease of life by putting linux on it but maybe it's not an option.

Thanks for all your help.

EDIT- Just found the specs and they really are terrible. 2.8ghz pentium 4, 192mb ram, ATI Mobility Radeon 7000 IGP. So am I screwed...

---

### Post by 3602 on 2011-07-26
It's OK. I'm just up.
Yeah. OK, you have some vintage specs. Although you *should *think about upgrading your RAM a bit, that's too little for a P4.
Now, when you get yourself 256 or 512 maybe, try [Lubuntu]("http://lubuntu.net/"). It's a very light fork of Ubuntu suitable for such more aged computers.
If you run into problems with Lubuntu you can always come back here.

---

### Post by dino99 on 2011-07-26
follow this little help for installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by afrocod on 2011-07-26
Lubuntu it is. I don't know if I will upgrade it, I've got a nice macbook pro all spec'd out. This is just an old laptop I was going to throw out and I thought it might be nice to throw linux on it. Anyway thanks for all the help. Your a gentleman.

Dino that guide just zoomed straight over my head.

---

### Post by dino99 on 2011-07-26
you probably need to bypass some acpi conflict. Add noacpi or nomodeset when installing.

---

### Post by afrocod on 2011-07-26
@dino99 How would I add that Dino?

---

### Post by 3602 on 2011-07-26
I believe pressing whatever key during the icon
"Keyboard equals Human"
will bring up a more flexible menu.
I believe that pressing *e* while on the Install Ubuntu line will give you a line which you can edit.
Problem is,
Do you *ever* get *any* graphics? If you don't then there's really nothing that you can do.
Also I see no correlation between that guide and OP's problem. No offense.

Also, Pentium 4 isn't old. It's still selling here in Quebec (some P4 computers being *more* expensive than Core computers). I believe you have too little RAM and generally RAM sticks are of cabbage price if you grab a generic one (usually harmless).

---

### Post by Miljet on 2011-07-26
Why don't you try Puppy Linux or DSL on that machine? Better than just tossing it out.

---

### Post by 3602 on 2011-07-26
Yep. You can also try [Klaus Linux]("http://www.knoppix.net/").
The benefit of this particular type of Linux is that nothing is installed to your hard drive. Everything operates from your CD.

---

### Post by afrocod on 2011-07-26
Cool, I'd rather do something with it than throw it out. Thanks for the suggestions. I'll give those a try.

---

### Post by afrocod on 2011-07-26
OK, just for the sake of completeness. That screen has finally stopped scrolling after hours and it shows the following. (I'm unsure whether this is even useful but, no stone left unturned, you know...)

[[IMG]http://farm7.static.flickr.com/6131/5977597839_c3d7ffd999.jpg[/IMG]]("http://www.flickr.com/photos/65633479@N03/5977597839/")
[IMG_2501_1]("http://www.flickr.com/photos/65633479@N03/5977597839/") by [C.P. O'Donnell]("http://www.flickr.com/people/65633479@N03/"), on Flickr

---

### Post by afrocod on 2011-07-26
@3602 I'm about to go out and get myself 1GB of ram because that's the most it can take. Now when I put this in will I be able to run the latest version of Ubuntu or will the rest of my spec's let me down.

---

### Post by afrocod on 2011-07-26
So I tried the Lubuntu disk and I finally got something

[[IMG]http://farm7.static.flickr.com/6017/5978002797_005e7ff900.jpg[/IMG]]("http://www.flickr.com/photos/65633479@N03/5978002797/")
[IMG_2502]("http://www.flickr.com/photos/65633479@N03/5978002797/") by [C.P. O'Donnell]("http://www.flickr.com/people/65633479@N03/"), on Flickr


So I tried the test memory and everything checked out. Then I tried Install Lubuntu and I get the same old scrolling black screen file name thing that I detailed before. Could anyone tell me what that indicates. Does it mean it's the graphics card that is the problem instead?

---

### Post by 3602 on 2011-07-26
Yeah, OK... Try "Try Lubuntu without installing". I've seen people running Ubuntu proper on a Cyrix 250 and 3dfx Voodoo 3 before...
I really don't know. We need a senior analyst.

---

### Post by afrocod on 2011-07-26
@3602 No luck. The first 3 options all give me the same scrolling screen as before.

---

### Post by Elfy on 2011-07-26
> **dino99 said:**
> you probably need to bypass some acpi conflict. Add noacpi or nomodeset when installing.

> **afrocod said:**
> @dino99 How would I add that Dino?

[https://help.ubuntu.com/community/BootOptions#Changing%20the%20CD%27s%20Default%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Changing%20the%20CD%27s%20Default%20Boot%20Options)

[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

Just so you know.

---

### Post by afrocod on 2011-07-26
So I've also got these F6 options but I'm afraid to touch them because I don't know what they mean.

[[img]http://farm7.static.flickr.com/6004/5978074775_a8e048b360.jpg[/img]](http://www.flickr.com/photos/65633479@N03/5978074775/)
[IMG_2503](http://www.flickr.com/photos/65633479@N03/5978074775/) by [C.P. O'Donnell](http://www.flickr.com/people/65633479@N03/), on Flickr

---

### Post by Blasphemist on 2011-07-26
First things first. Your initial issue is not enough memory.

Lubuntu 11.04 can be run with as little as 128 MB of RAM, but requires 256 MB of RAM to install from the graphics installer. The low memory that you have is the first issue to address. Even as light as Lubuntu is you don't have enough unless you have added some now. If you go to 1GB you will have enough for Lubuntu or another lightweight distribution of linux (distro). I don't recommend that you move forward without adding memory but it is possible.

Adding a gig of memory should be cheap and if possible, do it. In the end you aren't going to have a real strong pc even then. This could be quite useful machine even still. Let us know how you want to move forward and we'll help for sure. Personally, I would spend the money for an apple product. Try looking at this site, System76. [http://www.system76.com/index.php?gclid=CIfBhZLFn6oCFQllgwodUQzt6A](http://www.system76.com/index.php?gclid=CIfBhZLFn6oCFQllgwodUQzt6A)

I also saw a Toshiba Satellite at Best Buy the other day for $400 that temped me but I may just be cheap/poor.

---

### Post by afrocod on 2011-07-26
@[Blasphemist]("http://ubuntuforums.org/member.php?u=1165520") Oh I have a very nice Macbook Pro. This is just a secondary old laptop I was going to throw away but I thought it would be fun to set it up with Linux and give it a new lease of life.

---

### Post by afrocod on 2011-07-26
@[Blasphemist]("http://ubuntuforums.org/member.php?u=1165520") So you reckon that gig of ram is the cure to the Linux installation blues.

---

### Post by Blasphemist on 2011-07-26
I took a quick look around. You can go for distributions that will run with the little memory you have but there are limitations. For instance browsing the internet may not be what you expect. Here [http://www.slitaz.org/en/](http://www.slitaz.org/en/) is the number one recommendation from here [http://www.tuxradar.com/content/whats-best-lightweight-linux-distro](http://www.tuxradar.com/content/whats-best-lightweight-linux-distro) But yes, your memory is the issue now.

---

### Post by afrocod on 2011-07-26
@[Blasphemist]("http://ubuntuforums.org/member.php?u=1165520") So of all the light versions of Linux, Slitaz is the no. 1 pick. Is there a general consensus on that viewpoint or is it your own personal recommendation.

Thanks for the help mate.

---

### Post by Blasphemist on 2011-07-26
No I don't have any experience with those light distros. That is just the recommendation of that site. I don't think I'd be happy with those light distros. I did install and try Xubuntu and Lubuntu and I wasn't happy with them. I like Unity and Gnome Shell best though and that is certainly not everyones preference. In the end for me it's what is the best I can do on my hardware. If I need to add memory and can, I do for pc's that are real low on it.

---

### Post by 3602 on 2011-07-26
You could always try CrunchBag, that looks light enough (it's black and white and all).

---

### Post by JollyRoger1 on 2011-07-27
So were you able to get it installed?  I'm having the same problem only a slightly different error number.  I think my number ended in 04.  I believe it's the graphics card.  I also have an older laptop.  The one thing I did notice that it seemed to be all ubuntu / debian based linux os's.  I tried most all of them and ran into the same problem with all of them.  I am able to install non ubuntu / debian bases os's.  Such as PClinux,  Mandriva, Fedoria, Suse to name a few and was able to install Windows 7.  I'm hoping someone came up with a work around.  I'd really like to try ubuntu.

---

### Post by afrocod on 2011-07-27
@JollyRoger1 I just installed puppy linux on it last night. No hassle doing that. I definitely need more RAM if I want to move forward with any other heavier distro. I've only got 192mb in it. I might go out and buy a gig today but then again I might not. I'll let you know how it goes if I do.

By the way, that number changed for me twice. I used two different types of CD's and two different laptops to burn them so I think it's just a code on the CD and the rest is the information it is trying to read off of it.

Also if you can make it to the first installer screen which involves hitting any key when you see the "keyboard=human" icon before all the crazy scrolling stuff. Then hit F6 for other options. Select acpi=off or noacpi. Then install. I was able to make it to the next screen without the scrolling wall of text. I couldn't get any further but yours might be able to. I think my RAM let me down at that point.

---

### Post by JollyRoger1 on 2011-07-27
Thank you for the tip.  I was able to hit F6 and clicked no ansi.  From there I clicked "try Ununtu" and it did boot up and it work.  So I installed.  After installation I reboted and got a purple screen.  Nothing seems to happen.  So now I'm off to search the forum to try to find the fix for that.
 
I read that Puppy Linux worked well.  I had fairly good luck with PCLinux.  I found it to be very responsive.  The only issue I had with that OS was I couldn't figure where it installed software it claimed to have installed.  I also couldn't find any icon to execute the program.

---

### Post by JollyRoger1 on 2011-07-27
update on the never ending install. After lunch I kicked the laptop back on to see what would happen. This time with the purple screen I had the normal start up menu options. I click recovery and the screen did the never ending screen roll. This time I wrote the error message down. It was 48002. I then pulled the plug and restarted. I got the startup screen again so I clicked normal startup. The purple screen came back up but this time it only stayed for for a minute and then it went to a black screen with a prompt. I have 2 gig ram so I don't think it is totally a memory issue.

---

### Post by Blasphemist on 2011-07-27
Jollyroger, I do think you are having a video issue and that the link to a thread posted earlier in this thread can help you. Please go to this thread and read the first 3 posts. I believe you'll solve or get the right direction for your issue. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by JollyRoger1 on 2011-07-27
I discovered that my laptop also has a bios issue of which there are updates for but only in the windows format.  The issue has something to do with the keyboard.  What is typed in comes out in jibberish.  So I scrapped the idea and decided to go a different route.  I moved the back up files from the d drive to the c drive and made the d drive the c drive and installed ubuntu on the desktop.

**WOW!  Nice job guys.  **:D      This is really nice.  I really like the new desktop and menu system and installing software is easy.  At least what I've done so far.   I have to go play and start looking at what it would take to switch over.

---

