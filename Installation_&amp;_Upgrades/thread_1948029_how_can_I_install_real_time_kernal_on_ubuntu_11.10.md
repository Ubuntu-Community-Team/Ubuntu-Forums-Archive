---
title: "how can I install real time kernal on ubuntu 11.10"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by forsubhi on 2012-03-27
[COLOR=Black]I have kubuntu 11.10 and I read that I have to execute this command to install realtime 
[/COLOR][COLOR=Black][COLOR=#666699]
[/COLOR][/COLOR]```
sudo apt-get install linux-image-rt linux-headers-rt
```[COLOR=Black][COLOR=#666699]

but 
[/COLOR][/COLOR]```
sudo apt-get install linux-image-rt
```[COLOR=#666699][COLOR=Black]

don't work and give me the message 

E: Package 'linux-image-rt' has no installation candidate

what is the problem ? [/COLOR]
[/COLOR]

---

### Post by Sylos on 2012-03-27
Hello there.

The rt kernels are not in the standard repos IIRC. You need to add alesio Boganis ppa to get at them.

See here for the ppa:

[https://launchpad.net/~abogani/+ppa-packages](https://launchpad.net/~abogani/+ppa-packages)

Cheers

---

### Post by jerome1232 on 2012-03-27
> **Sylos said:**
> Hello there.

The rt kernels are not in the standard repos IIRC. You need to add alesio Boganis ppa to get at them.

Cheers

Wow! When and why did that happen? Doesn't Ubuntu Studio need those kernels?

---

### Post by forsubhi on 2012-03-27
thank you very very much Sylos 
I'll try it

---

### Post by forsubhi on 2012-03-27
I execute 
sudo add-apt-repository  ppa:abogani/realtime 
then I execute 
sudo apt-get                  linux-realtime
and then I get the following problem 

[IMG]http://img7.imagebanana.com/img/92og50bw/Selection_031.png[/IMG]

---

### Post by forsubhi on 2012-03-27
I think this is helpful when I execute sudo apt-get 

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                                                                                                
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                                                                                                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                                 
  404  Not Found

---

### Post by forsubhi on 2012-03-27
this also appear 
in sudo apt-get update 

W: Failed to fetch [http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

---

### Post by forsubhi on 2012-03-27
how can I use 
[http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/precise/main/source/Sources)
instead 
[http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/abogani/realtime/ubuntu/dists/oneiric/main/source/Sources)

---

### Post by Sylos on 2012-03-28
Hello there. Sorry for the tardy reply - i had to get some sleep.

Before you tried to install did you update the sources list with "sudo apt-get update"?

I'll keep an eye out on this thread throughout the day.

Cheers

---

### Post by Sylos on 2012-03-28
> **jerome1232 said:**
> Wow! When and why did that happen? Doesn't Ubuntu Studio need those kernels?

Not sure - I know the current Ubuntu studio doesnt ship with Real Time kernel. Supposedly there have been advances in the generic that allow reasonable performance at low latency. Personally I like rt kernels, even though they may be a little behind the current generic.

Anyhow as I said, IIRC, ....so I could be wrong!

---

### Post by forsubhi on 2012-03-28
yes I execute the 
sudo apt-get update 
but I use kubuntu 11.10 , is there problem with that ?

---

### Post by Sylos on 2012-03-28
There shouldnt be a problem with using Kubuntu.

Could you try opening Synaptic package manager and search for the RT kernel from there?

---

### Post by forsubhi on 2012-03-28
when I open Synaptic message appear showing me problem like this 
[IMG]http://img7.imagebanana.com/img/92og50bw/Selection_031.png[/IMG]

then I search for rt and found this 
[IMG]http://img6.imagebanana.com/img/d8p84drr/Selection_032.png[/IMG]

What should I do now ?

---

### Post by Sylos on 2012-03-28
Ok. 

So the third line down appears to be latest RT kernel available. I would say select and install it.

A couple of things to note: Dont remove any older kernels - if the new one fails or lacks something you need you want to have the trusty old one to fall back on.

Also, if you havent done this before you may not know that you will want to select the new kernel in the GRUB boot menu. It will normally be the first on the list unless you have set up GRUB differently.

Let me know how you get on.

EDIT: As far as the errors are concerned they appear to be based on hardy repos. Hardy went end of life years ago and so the repos will no longer exist - hence the errors. Did you add these repos yourself?

---

### Post by forsubhi on 2012-03-28
I think that I confuse you ;

I face this new errors 
[IMG]http://img7.imagebanana.com/img/uqbtw345/Selection_033.png[/IMG]


and if I use ubuntu software center 

The following packages have unmet dependencies:

linux-rt: Depends: linux-image-rt (= 2.6.24.31.33) but it is not going to be installed
          Depends: linux-restricted-modules-rt (= 2.6.24.31.33) but 2.6.24.31.33 is to be installed

[IMG]http://img7.imagebanana.com/img/txo1y9o4/Untitledwindow_034.png[/IMG]

What should I do ?   ](*,)](*,)

---

### Post by forsubhi on 2012-03-28
this error appear when I try to install linux-restricted-modules 
[IMG]http://img7.imagebanana.com/img/e5ww7j47/Untitledwindow_035.png[/IMG]

---

### Post by forsubhi on 2012-03-28
Note : I try to install linux-image-2.6.24.27-rt and I see it when I restart but when I select it the computer hanged and didn't complete boot process

---

### Post by Sylos on 2012-03-28
Hmm that is not what I was expecting.

I have to bail for the night now - but could you post up what software sources you have in use? I will try and look in again tomorrow.

Cheers

---

### Post by forsubhi on 2012-03-28
I didn't understand what do you mean by software sources , can you explain more ?

---

### Post by forsubhi on 2012-03-29
Is this helpful page  ?

[IMG]http://img7.imagebanana.com/img/7tpbpeud/Selection_039.png[/IMG]

---

### Post by Sylos on 2012-03-29
Hello again.

You could certainly download the kernel package from the PPA and install it - although the page your screen shot appears to show is for Precise - the version after 11.10 which you mentioned in the title of the thread. You would want Oneiric.

I am a little concerned as to why you have a broken package system. I think we should try to fix this.

Try the following:

Open Synaptic.
Choose Edit > Fix Broken Packages from the menu.
Choose Apply Marked Changes from the Edit menu or press Ctrl + P.
Confirm the summary of changes and click Apply.

The software sources I mentioned in my previous post are the PPAs that you have enable from which you download the software with apt-get or synaptic. I wondered if the hardy ppas you appear to have could be causing your trouble.

Try the fix above and let me know what happens.

Cheers

---

### Post by forsubhi on 2012-03-29
I execute 
sudo add-apt-repository  ppa:abogani/realtime 

then when I open synaptic, there is no broken packages, and when I select linux-rs to be installed and Choose Edit > Fix Broken Packages from the menu , this error appear 
[IMG]http://img7.imagebanana.com/img/xlwlks55/Selection_040.png[/IMG]


is there no real time for Oneiric or What ? 
and what is the difference between linux-rt and linux-image-2.6.24-30-rt which I installed it 

see this 
[IMG]http://img7.imagebanana.com/img/ckbtkovv/Selection_041.png[/IMG]

and could I install hardy software and how ?

---

### Post by forsubhi on 2012-03-29
[SIZE=2]I remembered that I add **ppa:abogani/broken  **to my repository and I have Question about linux-lowlatency                is it helpful for real time 

in the [https://launchpad.net/~abogani/+ppa-packages]("https://launchpad.net/%7Eabogani/+ppa-packages")
there is a lot of ppa , did I choose the correct one ?
ppa:abogani/realtime 

[/SIZE][SIZE=2]I want to install rtsj on ubuntu 11.10 and that's All , if there is another way to do that please tell me[/SIZE].

---

### Post by Sylos on 2012-03-30
Ok.

I have just had a look at the Oneiric rt kernel entry on Boganis Launchpad PPA page - This particular ppa is designated "broken" and has a message saying "never use". So I guess you should remove it from your list.

It does appear that there are no working rt kernel packages for Oneiric - Im sorry i didnt know this (I use 10.04 Luci Lynx for my studio set up). I also wouldnt have thought the broken packages would have been available through synaptic.

It seems that most of the ppas are broken - the only ones with an RT kernel that arent broken are for precise.

It is possible to build a kernel with the RT patch yourself using the vanilla kernel source but I have to be honest and say I would be out of my depth to help you if it went wrong. So Im not going to recomend you do it. Feel free if your brave and dont have valuable info that could be lost.

Not sure what would happen if you tried to install the precise rt kernel - theres liable to be some incompatible code in their. As far as I am aware if it fails then your system would just fail to boot into that kernl - your old kernel should still work. BUT THIS IS JUST WHAT I THINK IS THE CASE - kernels are normally pretty self contained so shouldnt mess with anything else - BUT TRY IT AT YOUR OWN RISK.

Sorry to have turned out not to be very helpful - I tried my best but my knowledge is limited.

Best of luck.

---

### Post by forsubhi on 2012-03-30
thank you friend 
I'll try to install 12.04  beta 2
Do you recommended this or not ?

---

### Post by Sylos on 2012-03-31
I dont have any experience of using it. The final release date isnt until April 26th so you could experience some breakage between now and then but I guess the only way to find out will be to try.

I know that as far as Ubuntu Studio is concerned, many people have been recommending use of 10.04 over the newer releases due to bugs and performance issues - but others have been quite happy with the newer releases - I assume it depends on what you are doing and whether your hardware is working ok.

Why are you trying to use the RT kernel? Have you tried using the vanilla kernel? You could find that it works ok for your purposes depending on what you do with it. Also, if you are having problems with it you could start a specific thread in the Ubuntu Studio section of the forum - people with a LOT more knowledge and experience than me frequent there and may be able to help with configuration and optimisation. 

I recently installed 10.04 on my newly built rig and was able to easily install the preempt kernel (this is know as a soft real time kernel rather than the RTKernel which is a hard realtime kernel - I cant explain the difference Im afraid). Sadly I appear to have a faulty motherboard that Im trying to get replaced so I havent been able to do full testing but the kernel installed fine without breakage and and appear to be able to run the system satisfactorily.

There are issues with using such an old release and kernel - security fixes and some newer features may not be available. I dont run it as my main system - I dual boot Ubuntu 11.10 and Ubuntu Studio 10.04 - I only use studio 10.04 for audio production so Im not too concerned by security issues as anything security critical is done on the up to date 11.10 system.

If you can use the vanilla kernel without issues then for now I might be tempted to stay with it until Precise 12.04 comes out and is stable - then maybe try moving up to it.

---

### Post by forsubhi on 2012-03-31
thank you  for your effort

---

