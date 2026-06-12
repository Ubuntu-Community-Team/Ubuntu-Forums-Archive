---
title: "GRUB2 bad problem!"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by Goldfish! on 2010-01-13
Finally got a dual boot on this laptop the way I liked it (LOVE my Win7, really like UBUNTU for certain things like getting booted and on the net fast...great). As I was editing and rebooting the GRUB settings UBUNTU got it's updates and installed (including one on GRUB that I hadn't seen before - WITH WARNINGS). Now I can't seem to get this last entry out of the boot menu:
vmlinuz-2.6.31-14-generic. It has all this listed now (had dual entries for everything like mem test before):

vmlinuz-2.6.31-17-generic
vmlinuz-2.6.31-14-generic
Windows 7

I got rid of the extra entries like memtest and all using:

sudo chmod -x /etc/grub.d/20_memtest86+

and such variations..still though I got one stuck in the boot selections.

It won't remove the old linux vmlinuz-2.6.31-14-generic build entry from GRUB (and they both point to the same place). It has a -14 and -17 entry in it now. Like I said both load to the same mount point.

Any help? I'm not a total n00b or stupid but this is driving me batshat...I mean I removed like five extra entries from GRUB using that command after the update (and had done it before about two months ago) but the linux vmlinuz-2.6.31-14-generic selection won't leave the GRUB selections now.

Any ideas? Thanks in advance. I really thought I had it figured out to the bomb having my laptop dual booting before, just didn't like how UBUNTU used my disk space by default last time so I decided to rebuild the laptop. Really any help getting rid of the extra entry in the boot selection would be great.

---

### Post by darkod on 2010-01-14
Usually you would leave at least one older kernel that's working fine in case the latest one starts giving you trouble. That way you can boot previous kernel and have the system operational.

But if you still want to remove it I think you need to use Synaptic and remove the kernel itself. Not sure of the exact packages you need to remove, I think it was like:
linux-image-2.6.31-14
linux-headers-2.6.31-14

Google for "removing old ubuntu kernels" for exact procedure. Be careful what you remove.

After that when you do update-grub it will delete the entry with the kernel removed.

---

### Post by Goldfish! on 2010-01-14
Thanks, that actually makes sense leaving the old build in there so I'll just leave that alone.

Any advice on changing splash screens and login screens easy? Same Ubuntu...any help? I'm a graphics guy and I get that a lot of what I am trying to do just replaces graphics and all. I tried peeking at the Linux partition in WIN7 but none of the programs out there looking at EXT formats seem to like it much.

Guess what I am looking for now is something that likes WIN7 and can see UBUNTU too. Don't tell me the 'top three'...they don't work with win7.

---

### Post by darkod on 2010-01-14
> **Goldfish! said:**
> Thanks, that actually makes sense leaving the old build in there so I'll just leave that alone.

Changing splash screens easy, changing login screens. Same Ubuntu...any help?

Are you asking me about changing login screen and splash screen? Know nothing about that sorry.
But there surely are tutorials on google.

---

### Post by Goldfish! on 2010-01-14
No your answer was right. It makes sense to leave an old useful kernel where it was. I found the permanent links to that in the file system and decided to leave it alone, could get rid of it but like you said it makes sense to leave it alone for a bit.

The other crap I am trying to mess with is just 'prettying up' Ubuntu. Something like making users who look at it on my laptop not wonder WTF it is since they are used to seeing...Windows.

The idea of Windows VS Linux distros. It is really not that hard, no harder than trying to teach someone how to use their new and more advanced cell phone after they have been latched onto an old one for three years. Still though...Ubuntu could be more cross-platform friendly. Standards...what users are used to seeing.

Probably not the first person to ever wish there was a seamless windows-linux something or another (oh yeah...no I am not). Still though Ubuntu comes so close. What is missing?

Now that sounds like bitching...

I'd like to edit my splash screens and login screens. The version of Ubuntu I am using says no way...even if I try SU...I might be putting commands in wrong.

---

### Post by presence1960 on 2010-01-15
> **Goldfish! said:**
> No your answer was right. It makes sense to leave an old useful kernel where it was. I found the permanent links to that in the file system and decided to leave it alone, could get rid of it but like you said it makes sense to leave it alone for a bit.

The other crap I am trying to mess with is just 'prettying up' Ubuntu. Something like making users who look at it on my laptop not wonder WTF it is since they are used to seeing...Windows.

The idea of Windows VS Linux distros. It is really not that hard, no harder than trying to teach someone how to use their new and more advanced cell phone after they have been latched onto an old one for three years. Still though...Ubuntu could be more cross-platform friendly. Standards...what users are used to seeing.

Probably not the first person to ever wish there was a seamless windows-linux something or another (oh yeah...no I am not). Still though Ubuntu comes so close. What is missing?

Now that sounds like bitching...

I'd like to edit my splash screens and login screens. The version of Ubuntu I am using says no way...even if I try SU...I might be putting commands in wrong.

Sorry goldfish but Linux's strengths lie in it's differences from windows. It is those differences that make it what it is. To make linux more windows-like will be the end of it. May that day never come. Read [this]("http://linux.oneandoneis2.org/LNW.htm").

As far as making Linux cross platform friendly- what are you thinking?

---

### Post by Goldfish! on 2010-01-15
I know the idea and concept of making Linux more 'windows like' is redundant man, but this isn't my first Linux / Unix rodeo either. I had high hopes for BeOS way back when because it was a good shot in the direction of a totally independent OS though.

Linux as an OS and the GUI have become more 'windows' familiar and it has been both a good and bad thing, however mostly I think it has been going towards a GOOD thing. It isn't good for techies and tinker type people because we like to think and know that we can be on the inside out of the computer but it is good as far as making headway to users becoming familiar with it.

Ubuntu does a lot to bridge that distance and I have been playing with it because of that for quite awhile. It has now gotten to a point in it's development that I can actually be comfortable booting into it and letting a client use it without being confused about what they are looking at. It is more common that I get a question like 'Why are you using this?' than 'Where the hell is (fill in the blank)?'.

I'd like to be able to see a Linux distro I could just boot into and have no questions asked about how to use it and such should someone not tech fit sit down and try to use it. That is the reason I am asking the questions I am asking. Ubuntu is pretty user friendly and I don't get much BS about it but seriously it could be more familiar to users who aren't all that techie.

Booting up a PC, powering on a cell phone, and all that comes in between those things makes first impressions on people. If it looks cumbersome or unfamiliar people are going to go into instant 'DO NOT WANT' mode.

Again I know what you are saying and Linux in general should not be a Windows clone for all the right tech reasons. However it should be (in my opinion) something seamless to an end user who doesn't care about the clockwork underneath the computer they are trying to use.

Aw hell, you got me after my morning coffee...sorry about that. But seriously it is why I am aiming at doing what I am doing. Making something as familiar as possible out of Linux for the average PC user.

---

### Post by presence1960 on 2010-01-15
> **Goldfish! said:**
> I know the idea and concept of making Linux more 'windows like' is redundant man, but this isn't my first Linux / Unix rodeo either. I had high hopes for BeOS way back when because it was a good shot in the direction of a totally independent OS though.

Linux as an OS and the GUI have become more 'windows' familiar and it has been both a good and bad thing, however mostly I think it has been going towards a GOOD thing. It isn't good for techies and tinker type people because we like to think and know that we can be on the inside out of the computer but it is good as far as making headway to users becoming familiar with it.

Ubuntu does a lot to bridge that distance and I have been playing with it because of that for quite awhile. It has now gotten to a point in it's development that I can actually be comfortable booting into it and letting a client use it without being confused about what they are looking at. It is more common that I get a question like 'Why are you using this?' than 'Where the hell is (fill in the blank)?'.

I'd like to be able to see a Linux distro I could just boot into and have no questions asked about how to use it and such should someone not tech fit sit down and try to use it. That is the reason I am asking the questions I am asking. Ubuntu is pretty user friendly and I don't get much BS about it but seriously it could be more familiar to users who aren't all that techie.

Booting up a PC, powering on a cell phone, and all that comes in between those things makes first impressions on people. If it looks cumbersome or unfamiliar people are going to go into instant 'DO NOT WANT' mode.

Again I know what you are saying and Linux in general should not be a Windows clone for all the right tech reasons. However it should be (in my opinion) something seamless to an end user who doesn't care about the clockwork underneath the computer they are trying to use.

Aw hell, you got me after my morning coffee...sorry about that. But seriously it is why I am aiming at doing what I am doing. Making something as familiar as possible out of Linux for the average PC user.

The sad truth is about one half of the average PC users don't even have a clue about the OS most of them use- Windows. Making something more familiar which the person does not understand to begin with is futile in my opinion. Most PC users expect everything to just work and unfortunately with windows even if it does initially it does not last. I have developed a decent work at home part time business working on PCs. The vast majority of my work is from Windows users who for the most part know how to turn the machine on and point & click a few things. They do not know even the basics about windows and do not want to learn. They look at their PC like a toaster- they put the bread in depress the handle and expect toast. Unfortunately as you and I know that is not the reality of a PC. Trying to make Linux more Windows-like will only disappoint & frustrate the majority of Windows users who try linux and just create unfavorable word of mouth advertising against Linux. We all know word of mouth is the most powerful form of advertising or promotion.

This is why I believe we need to stick our ground. The best "sales" approach is not to emphasize the failings of your competitor but rather to "sell" the things that your product can do which will enhance the experience of the "purchaser". In this respect it is exactly the differences between linux & windows that make linux a better OS. A final word I try to live up to: To thine own self be true!

P.S. Never forget this: Linux is not for everyone, just as windows is not for everyone. I could not care less if Linux ever catches up in market shares with windows or Mac. I use linux because I choose to. I am not part of a movement that wishes to overtake windows nor convert windows users. Those who will come to linux will probably come because they truly want a better OS. That is why I am here and for no other reason. We can talk about freedom and choice, but the bottom line is most of us want a better experience running an OS. Let's not ever lose sight of that and think that our mission is to convert the PC world to linux. The principle of attraction rather than promotion will garnish more "converts" than anything we can say or do.

---

### Post by Goldfish! on 2010-01-15
> **presence1960 said:**
> 
P.S. Never forget this: Linux is not for everyone, just as windows is not for everyone. I could not care less if Linux ever catches up in market shares with windows or Mac. I use linux because I choose to. I am not part of a movement that wishes to overtake windows nor convert windows users. Those who will come to linux will probably come because they truly want a better OS. That is why I am here and for no other reason. We can talk about freedom and choice, but the bottom line is most of us want a better experience running an OS. Let's not ever lose sight of that and think that our mission is to convert the PC world to linux. The principle of attraction rather than promotion will garnish more "converts" than anything we can say or do.

It could be for everyone, and I really believe that. I'm not a hardcore Linux nut, and as a tech guy I actually hate the idea of trying to manage it as it stands for an end user right now. Too many flavors, too many options, confuses the **** out of business people who actually pay for this stuff.

As far as the point, click, done end users go yes I agree and have made my living off of them for 20 years in the Windows environment. Point, click, done. However they do get pissed and frustrated at the unfamiliar.

Yes like you, I am a tech guy, and I have my MCP and MSCE's to prove it. Microsoft made me my living and I  won't deny that. Good on them...great business model. GOOOO MICROSOFT!!! Keep standardizing your stuff!!!!

However I have actually taken a PC out of dumpters specifically to do things like run Oberon OS and Reactos, plus many Linux variants back when drivers were not so easy. My Frankenstiens...I loved them all.

Linux does offer something more customized and secure. WINE in itself admits Microsoft has a corner on the market of familiarity.

Got to be a happy medium somewhere.

People happy using Linix / Unix drones on their smart phones who are totally confused about using their computers and vice versa. That is Linux vs Windows.

Somewhere there is happy medium 'open' ground with standards. I believe that.

Someone come up with a standards and business model for Linux and have it made in the shade.

Oh and I hacked the splash...now to the login...SUDO not just SU anymore.

---

