---
title: "Upgrading problem issues with hardware ??"
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by hebdave on 2015-07-01
The after upgrading problems- On upgrading I do eventually get a login screen but the password box reverts or jumps to the guest user repeatedly on trying to enter password details. Not only this the screen stays black up to 3-5 minutes before even allowing me to attempt a password entry with a visible graphic screen. It could be a graphics stability problem although I don't no enough about computers.

Hi I wanted to know if I should keep my old configurations when asked during an upgrade from 12.04 - 14.04 instead. Can an update be responsible for my older hardware to then not work perhaps ? - my monitor does work with 12.04 okay by the way. Or could it be my BIOS or bootloader issues ? My computer is older and has XP as the foundation for my Ubuntu install. Although XP is unused since its last windows update as its a personal computer. The grub appears to work okay on selecting Ubuntu or windows choices and is shows up well straight away. So as described its once its fully booted the black screen stays for a long length of time etc (see first paragraph).

Thanks very much indeed.

---

### Post by dino99 on 2015-07-01
have you rebooted after the last upgrade ?

---

### Post by hebdave on 2015-07-01
Yes its been booted several times. My system information is this -

Memory- 2.8 GiB
Processor - AMD Athlon(tm)64 X2 Dual Core Processor 3800+ × 2
Graphics - Unknown
OS type - 64-bit
Disk 94.9 GB

The correct graphics driver is installed as recommended. NVIDIA accelerated graphics driver. 

I have restored an image alongside XP again of Ubuntu 12.04 so we can start from square 1 and find the best way to update - either with or without old configurations. I am not concerned in keeping any applications or keeping any particular set ups but wonder the best way to sort this . 

The other thing I should mention is I did have 14.04 up and working until one week ago when a system update caused my grub to disappear. So I then, like today, restored 12.04 so I could upgrade it again. This time I did get the grub back but then had the problems outlined in my first post above.

I am not sure if at some point we will need to use a live cd to help fix the update issue if you ask me to try and upgrade again. Although I am unclear whether I need to use the grub based restore function or a live cd here. Also I do not know how to use the live cd to fix anything as yet but can follow guidance instructions if required. I do have hirens boot and other alternatives available via a usb stick to fix anything but have never used them and don't no how to do so. 

I also use multi boot yumi software which can add anything else you might require to help me potentially fix anything should that become necessary. I of course hope its a simple issue in upgrading correctly and no grub restore or live cd will be required. Again I don't know much about any of the tools I have on the yumi multiboot stick.

Thanks very much.

---

### Post by hebdave on 2015-07-02
157 views am I saying something confusing ?

---

### Post by howefield on 2015-07-02
> **hebdave said:**
> 157 views am I saying something confusing ?

Actually, yes you are, but we won't go in to that right now.

Just to say that 2 forum members other than dino99 have viewed your thread, the rest are either search engine spiders or guests, both of whom will have great difficulty in replying even if they wanted to. So don't feel bad, yet.

Did you remove the nvidia drivers prior to upgrading ?

---

### Post by hebdave on 2015-07-02
Are okay sorry about that. In answer to your question - No I did not remove anything. What I can tell you is that 14.04 has always worked up in till the recent update I gave it. So I used parted magic to delete the ubuntu partition and the unmounted swap. This left me with unallocated space and a quick fix needed with ubuntu wiki recommended boot-repair program via usb. I had to do that to be able to boot into windows again as I got a grub rescue problem since the ubuntu partition was removed. So I have a fully updated XP up till one year ago when support stopped for it. Then I used a usb key with a multi-boot based on the "yumi" software to install the newest iso of 14.04. This had worked prior with the older 14.04 iso via yumi. I had to then install using the installer since "try ubuntu"
does not work. This time I did not ask to use the updates offered by the installer as this could put me back to square 1 with the updates issue I have. 

So far I have a shaky graphics where the screen nearly freezes. In the past I think I searched for the drivers without making to many rapid movements and key presses and installed the recommended nvidia graphics card. This I think should fix that as it normally does. I will refrain from doing this though if you'd can guide me from here if you'd prefer. It potentially could be a number of computer issues if its not related to the updates. Also I can revert the graphics to 2D unity, I think people call it, if you show me how. It could be a desktop problem I read on Google but maybe not that either.

My experience of Ubuntu is limited and the above computer skills are developed from asking and learning ways round grub problems in conjunction with booting windows. So I honestly no much much less about computers than it first may seem. Ironically I have ended up with hirens boot on the yumi multi boot and all sorts not knowing what to do with any of these tools in reality. Although I use parted magic clearly so I have learnt tiny bits.  Any way this last paragraph bears little relevance to my problem questions above.

Many thanks I will keep me answers shorter from now on.

---

### Post by grahammechanical on 2015-07-02
There is a saying: If you find yourself in a hole - stop digging.

Deleting a Ubuntu partition without first re-installing the Windows boot loader to the hard disk will get us to a Grub rescue prompt because we have deleted the files that Grub needs to produce a boot menu. 

Unity 2D is not available in Ubuntu versions after 12.04. When we upgrade to a newer version of Ubuntu as from going from 12.04 to 14.04 or doing a fresh install of 14.04 we get newer Linux kernels and if we are using a proprietary video driver we will get newer proprietary video drivers. That is fine if those newer drivers support our video card. But sometimes support for older cards is dropped from newer drivers. It has happened in my case and it maybe the situation you are in. 

If you do a fresh install of 14.04 do not tick the box Install third party software. Then Ubuntu will run with an open source video driver. After the installation has finished we can get those video and audio codecs by installing Ubuntu Restricted Extras from the Software Centre.

If you re-install 12.04 do not use a proprietary video driver when upgrading to 14.04. If you still have 14.04 installed, then at the Grub boot menu select Advance Options for Ubuntu and then select Recovery Mode. At the recovery menu select Resume. That will load Ubuntu with an open source fall back video driver called llvmpipe. Now we can go to Additional drivers and change video drivers.

Regards.

---

### Post by hebdave on 2015-07-03
EDIT : Below is less relevant now as I think I have misunderstood what you wanted me to do. Although its worth a reading. I think you did mean install the XOrg (or similar) open source driver found in "additional drivers". As now my screens gone black again on re-booting after installing the nvidia recommended proprietary driver again. The same black screen happens on re-boot using Ubuntu restore and resume now. The black screen means I can't currently change it back to the Xorg open source driver in additional drivers, the other option, which would give me graphics back at least. I think that has to be done first and then [COLOR=#000000]installing Ubuntu Restricted Extras from the Software Centre perhaps in restore mode too? . How do I do this now ? My sincere apologies. Perhaps read the below to see why I was confused a bit. I promise to ask before and act after from now on.[/COLOR]

High due to my computer knowledge I am still a little hazy about what "propriety" means in the context we are talking about. I did look up the dictionary meaning of the word but am a little unsure still in this context. Since I have 14.04 installed I have used "resume" and then "additional drivers". This is currently now installing NVIDIA legacy binary driver - version 304.125 from Nvidia-304 (which is **proprietary tested**). There is however as you know a warning at the bottom of that graphical interface saying - 

A Proprietary driver has private code that developers can't review or improve. Security and updates are dependent on the driver vendor. Are you suggesting I still use the proprietary tested ( Nvidia owned driver ) until they stop support for it. Or are you saying if you prefer use [COLOR=#000000]video and audio codecs by installing Ubuntu Restricted Extras from the Software Centre. Is restricted extras already installed since I do seem to have an open source offering in my additional drivers - **should I use the open source one and is this the whole point of what your saying really.**[/COLOR]

[COLOR=#000000]And if I use Ubuntu restricted extras does this need installing still ? Would this insure any further issues with support for any drivers required in the future ? The computer concerned is a bit pre-historic at about 10 years old. Last time with the shaky graphics I did manage to install the drivers without using the restore options in ubuntu falling back to the [/COLOR][COLOR=#000000]llvmpipe driver. So I hope one of the drivers if we need to change to the open source one instead will fix "the overall computing problem". [/COLOR]

[COLOR=#000000]Should I still update Ubuntu now or not as that was the original issue that stopped 14.04 working initially I presume ?[/COLOR][COLOR=#000000]

Many thanks.[/COLOR]

---

### Post by howefield on 2015-07-03
Might be worth knowing what the video card is.. can you post the output of the following 2 terminal commands..

```
sudo lshw -C video
```

```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by hebdave on 2015-07-04
Hi thanks I am using a live cd via hirens boot - the others like Ubuntus don't seem to work as they just let me install. They won't use "try ubuntu" to get access to the live cd. However what I am doing via the hirens live cd "that actually works" is giving me a terminal of course. Here is the output as you refer  -

```
root@PartedMagic:~# sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: C51G [GeForce 6100]
       vendor: NVIDIA Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:19 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff memory:febe0000-febfffff


```

and the desktop output I assume is your second one wanted. I am punching in the dollar sign found in conjunction with the no.4 key on my keyboard after the **echo** and a space. If its a different symbol on that one, where is it on my keyboard ? I cannot see it on looking for a while so may need direction if it is not a dollar sign to get you the output.

I could re-install Ubuntu again alongside windows and move forward with the other graphics open source driver rather than use nvidia. While the open source graphics driver may or may not work the Ubuntu Restricted Extras from the Software Centre package should be installable via restore mode> resume as well. Otherwise hopefully we can solve that output issue for the second part you need.

Many thanks.

---

### Post by hebdave on 2015-07-05
Hi I am not sure what I am doing. I read what I last wrote to see if it was over done and a bit assuming. It was a bit. So sorry about that I need to stick to answers required and not go off on tangents. 

I was saying that I struggled with getting the second output basically. So when I type in echo $XDG_CURRENT_DESKTOP that does not work. I assume after the echo part and the space that is a dollar sign. If it is not can you tell me what this is and where it is found on the keyboard ? Is the end conclusion of what we are doing to install the Ubuntu restricted Extras ? Would this give proper open source graphics then ? Or was the open source driver I found in "additional drivers" the only required thing ? Or are we now taking a different route with things since I may of been correct installing the nvidia driver as I had ?

I am sorry to have perhaps confuse people in my last post. I will attempt to be more concise without going in many different directions with what I am saying.

If you can perhaps still give me a hand that would be great. Otherwise I feel I am left not knowing if 14.04 is possible with my current hardware. Its a shame to not know either way whats possible for future things with ubuntu. Mind you its been only a day and half since my last post so it could be a busy time for you guys helping us all. Many thanks for all your efforts. :)

---

### Post by howefield on 2015-07-05
Please don't bother with the echo $XDG_CURRENT_DESKTOP command, I thought you were running Ubuntu in some form. Now I have not got a clue what you are running. I'd say if 12.04 is working for you, stay with it - it is supported for another 2 years almost.

---

### Post by hebdave on 2015-07-06
It is Ubuntu 14.04 that I am running. When you say in "some form" did you think I was running a different form of Ubuntu distro - eg xbuntu, Lubuntu or something ? 

What I do not understand is I had been able to run 14.04 for 1 year and then suddenly I did a normal apt-get update and it all disappeared on me ? 

Can you offer any explanation for this. Is it purely something to do with the Kernel ? Its seems quite frustrating to me. For example if it is the kernel then is there a variation of Ubuntu or some other linux distro I can use instead that works with a 10 year old computers and still updates ? 

Also and this is not the primary question (the others are)- How secure is a 12.04's system without the upgrade ? I once read somewhere it makes the kernel less protected or something. Also once its support runs out how safe would it remain ? 

I do feel there is a way to get the 14.04 working by missing out one sudo apt-get update perhaps that caused this. I could easily persist with this if you think its worth another discussion and a try. I can start again explaining if you feel I missed something or was confusing - just ask away... 

Coming to think about it I can access restore mode at root but not in the resume>graphics mode anymore. I think the restore root mode is as good a terminal as my live cd options perhaps- although I digress.

I do appreciate your time and help thank you.

---

### Post by hebdave on 2015-07-06
Right I have managed to do alot more this time and so hope you can help me with the idea of system updating to complete the install process. The driver now works with the nvidia ones. :)On re-installing again I have found that a different propriety updated (as they referred to it) works. It should be noted I was using the first 14.04 iso this time which might of helped as I think there was problems with the 14.04.2 latest iso (no doubt more advanced). I do not know if or when I should install the ubuntu apt-get updates however as this might cause a problem as it had before ? I hope you follow me and this makes sense- I am not talking about updating drivers as thats done. I was meaning shall I proceed with **all** the system apt-get updates as normal. Before when I added the full system updates I lost entry to Ubuntu, black screen etc- or at least that was what seemed to happen ? will updating from the terminal help perhaps ? Or can I remove an update that would potentially cause a problem for me ? Really hoping I can get some direction even if its to say "your not sure" so I know its could be 50 50.

Many thanks its so great I can boot now and have the restricted extras installed- I realised that was the same as the installation 3rd part extras in the end after a re-read graham mechanical post I think it was. Cheers guys if you can just confirm my conclusions I'd be most grateful. Also if this goes wrong how do I do regain access without re-installing again - what was that roll back thing people talk about ? - does that have some other meaning.

Thanks.

---

### Post by hebdave on 2015-07-08
High my problem is not fixed and solved. So I cannot mark it as solved as yet. I'd need to know a few important things before we can mark it solved-

Now I have an earlier iso of 14.04 that works with my graphics, solved from your prior help-

 Can I do system updates missing certain updates out which may cause hardware errors (assuming thats what was causing my prior problems)? Would missing certain updates affect security  ? Is it something to do with the kernel that I will never be able to update- was that Graham mechanicals **whole** point ? Should I attempt a full update once again to see if it works anyway this time ? - I could not tell from graham mechanicals post the full answer to all my questions  -

> [COLOR=#000000]When we upgrade to a newer version of Ubuntu as from going from 12.04 to 14.04 or doing a fresh install of 14.04 we get newer Linux kernels and if we are using a proprietary video driver we will get newer proprietary video drivers. That is fine if those newer drivers support our video card. But sometimes support for older cards is dropped from newer drivers. It has happened in my case and it maybe the situation you are in. [/COLOR]

I can tell that its hard to get the right driver because of his kind points. But I have now managed to get the right one and thats solved. But I am not sure if system updates will make some of my hardware defunct again. Can some updates be left out or will a full system update be best to try again first ? If there is no terminal command that can help us out before updating and there is no way round this then is it down to this -

Should I now use a different distro as already suggested ( I'd rather not of course) ?

If I do which one gets regular updates that work with my hardware most likely ?

Yes I am at a beginner level but I do feel I still need help. I can only rely on your goodness to guide me.

Please ask if you are confused as I did feel I over-explained in my initial "first" post and caused much confusion. I wondered if a new post in a new topic concisely done would now help ?

Thank you so much.

---

