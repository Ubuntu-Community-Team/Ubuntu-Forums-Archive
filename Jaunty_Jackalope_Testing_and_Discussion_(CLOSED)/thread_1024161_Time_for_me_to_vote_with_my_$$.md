---
title: "Time for me to vote with my $$"
date: 2008-12-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Naddiseo on 2008-12-28
I think it's time for me to get a new video card, and I'd like to go ATI this time around, to vote with my dollars so-to-speak. Does anyone have any recommendations for a decent ATI card that'll be forward compatible with jaunty and will last me at least a few years. I've switch my gaming to console, so I don't need a high end card, that being said, I do like eye-candy. I have two 22" monitors that I run at 3360x1050 (twinview) so I'd like to be able to continue that.

Also, how are the ATI drivers in jaunty at the moment? I know nvidia's wont even install for me, nouveau is lagging behind the latest kernel, and nv/vesa wont work with my motherboard (I think it broke with a bios update I did).

---

### Post by melojo on 2008-12-28
Nvidia drivers have better linux support than ATI, although ATI has made strides in the last year or so.  If you have problems with Nividia in Jaunty then I would think you would most certainly have the same problem with ATI.

I would stick with Nvidia thats my 2 cents.

---

### Post by Progressive on 2008-12-28
I personally think the open source ATI drivers are near perfect for what they do. If you want DRI2 and KMS right now, ATI can give it to you. 

The Catalyst drivers are very good for gaming, but obviously not open source and not without their little glitches.

Catalyst still has some known WINE issues. Either WINE or ATI will fix them soon since it is a known problem and they have already made some significant strides on it. 

In any event, when the open source drivers switch to Gallium3D, which should be in about a year's time, ATI should be able to handle most games. If you want an investment for the future, I recommend ATI.

Right now, outside of WINE, it is a coin-flip between the two proprietary drivers since both support accelerated and tear-free 2D/3D. Granted, it is claimed that if you are a 3D graphics professional you may see some issues with ATI, but I'm not qualified enough to know or care about that.

---

### Post by Naddiseo on 2008-12-28
> **melojo said:**
> Nvidia drivers have better linux support than ATI, although ATI has made strides in the last year or so.  If you have problems with Nividia in Jaunty then I would think you would most certainly have the same problem with ATI.

I would stick with Nvidia thats my 2 cents.

Yes, they may do *now*, but for how long? I've been having problems with nvidia drivers since Hardy, I'm using intrepid right now, clean install, and I can't use compiz because the hardware nor software cursor show. I've sent bug reports to nvidia about this. As I said before, the vesa driver just gives me a screen mess, and freezes my computer. I think I've bugged this too. Nv has been so ridiculously slow since intrepid at painting, it takes about 10 minutes to paint the gdm login screen. I've bugged this, but I think it's a hardware problem since my old dapper CD doesn't work now. Now, the nouveau drivers I like. They work most of the time, just a little slow at screen redrawing, and don't work with youtube flash videos. But I can live with that.

> **Progressive said:**
> I personally think the open source ATI drivers are near perfect for what they do. If you want DRI2 and KMS right now, ATI can give it to you. 

The Catalyst drivers are very good for gaming, but obviously not open source and not without their little glitches.

Catalyst still has some known WINE issues. Either WINE or ATI will fix them soon since it is a known problem and they have already made some significant strides on it. 

In any event, when the open source drivers switch to Gallium3D, which should be in about a year's time, ATI should be able to handle most games. If you want an investment for the future, I recommend ATI.

Right now, outside of WINE, it is a coin-flip between the two proprietary drivers since both support accelerated and tear-free 2D/3D. Granted, it is claimed that if you are a 3D graphics professional you may see some issues with ATI, but I'm not qualified enough to know or care about that.

Well, I can't say I use any Wine apps anymore, I used to play BF1942 through it, but I have a laptop with windows on, which I very rarely boot into so I can play some games. So, it does look like investing in an ATI card now, and supporting their open source-ness will be beneficial for me, and ATI.

---

### Post by doas777 on 2008-12-28
take this as you will, but a few months ago I decided to go ATI for an XP box, just because of the Nvidia GPU flaw scandal. I had heard they had gotten better for linux, so i figured I'd give em another try. 

I don;t know if it is Diamond or ATIs fault, but i had a terrible time getting it going. the only driver it will work with is the one on the disk. diamond is not the best.

overall I rather wish i had Nvidia card and taken a gamble.

---

### Post by melojo on 2008-12-28
> **Progressive said:**
> I personally think the open source ATI drivers are near perfect for what they do. If you want DRI2 and KMS right now, ATI can give it to you. 

The Catalyst drivers are very good for gaming, but obviously not open source and not without their little glitches.

Catalyst still has some known WINE issues. Either WINE or ATI will fix them soon since it is a known problem and they have already made some significant strides on it. 

In any event, when the open source drivers switch to Gallium3D, which should be in about a year's time, ATI should be able to handle most games. If you want an investment for the future, I recommend ATI.

Right now, outside of WINE, it is a coin-flip between the two proprietary drivers since both support accelerated and tear-free 2D/3D. Granted, it is claimed that if you are a 3D graphics professional you may see some issues with ATI, but I'm not qualified enough to know or care about that.

I have had ATI cards and Nvidia cards and I have always had problems with ATI.  I have never had any problems installing Nvidia drivers with the hardware I have had.  I am not running jaunty though.  I am glad that ATI has finally got their head out of their arss and started to take linux seriously.

---

### Post by cariboo on 2008-12-28
I have always had problems with ATI video cards, from as far bask as Windows98 and Redhat 5.2 ATI drivers have not been very good. I haved used Nvidia cards going back to the Riva and TNT, they have always just worked with my hardware, whether it is Windows or Linux.

Jim

---

### Post by MadsRH on 2008-12-29
I can't tell you what to do, but if I was going to buy a new card I would go for Intel. If you want hardware that just works on Linux - use Intel (in my opinion). Also Intel is the [largest Hardware Vendors contributing to the X Server]("http://www.phoronix.com/scan.php?page=article&item=x_server_contributors&num=2").

All that will be supported by KMS in the 2.6.29 kernel is Intel hardware. ATI does have kernel mode-setting support, but it's not ready to be merged into the mainline kernel due to its dependence on the TTM memory manager rather than GEM. We previously talked about the GEM-ified TTM manager for the ATI driver, but a new version of TTM must come about or the Radeon memory management code be redesigned so that it can be pushed upstream. If this work can be accomplished in the next three months we could possibly see it in the Linux 2.6.30 kernel. Any NVIDIA kernel mode-setting support is still a ways out since the third-party Nouveau driver depends upon Translation Table Maps as well and there isn't even a stable 2D Nouveau driver out yet. [Source...]("http://www.phoronix.com/scan.php?page=news_item&px=Njk2MA")

Just my 2 cent ;-)

---

### Post by Progressive on 2008-12-29
[http://www.phoronix.com/scan.php?page=article&item=amd_r600_oss_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600_oss_3d&num=1)

R600 and R700 documentation has just been released today that will allow open source 3D acceleration for the newest cards.

I have an X1000 series, so it doesnt affect me currently, but it should matter a great deal to anyone considering purchasing a new card.

I agree that ATI used to have abysmal linux support, but at least since their purchase by AMD they have been committed to open source drivers and support. Their developers are frequently responding to questions over on phoronix.com

Intel also has great open source support, but their chips are simply not up to par with ATI or Nvidia when it comes to gaming. If you don't care about gaming, go with Intel. 

If you care about gaming and open source equally, ATI is a good bet. If you care mainly about gaming above all else, Nvidia is currently the best, but ATI is hot on their tail and likely to surpass them. 

You have to understand how awesome Gallium3D is in order to understand why the future for ATI looks so bright. It is an architecture that allows graphics back-ends to be dropped in, allowing for instant support of the newest versions of OpenGL, GLSL, etc. Nouveau uses Gallium3D too, but they have absolutely no support from Nvidia.

---

### Post by RAOF on 2008-12-30
> **MadsRH said:**
> I can't tell you what to do, but if I was going to buy a new card I would go for Intel. If you want hardware that just works on Linux - use Intel (in my opinion). Also Intel is the [largest Hardware Vendors contributing to the X Server]("http://www.phoronix.com/scan.php?page=article&item=x_server_contributors&num=2").
...

Of course, this would be somewhat difficult because Intel don't actually *make* graphics cards, only integrated chipsets :).

---

### Post by marcgh on 2008-12-30
I'm a newbie running Hardy. I was running XP pro and my existing card is Sapphire radeon HD 4850. After downloading the linux driver and learning how to install it in console all worked perfectly. I only had to disable any desktop animations otherwise perfect. Also ATI has a pdf file explaining how to install.

---

### Post by salsafyren on 2008-12-30
I have an ATI radeonhd 3850 card and I'm using the radeonhd driver in Debian Lenny. Works perfectly for 2D now, no lock-ups whatever.
The proprietary driver fglrx locks up in my experience.

The reason I bought this card was exactly because of the open source work initiated by AMD at the time. It seems like it was a good investment if you look at the driver work done now and what is coming in the future.

The problem in choosing nvidia is that you'll probably never have an open source driver. So I would recommend an ATI card.

---

### Post by gnomeuser on 2008-12-30
I am in a situation where I unfortunately now am forced to use an nvidia card as that was what came with my laptop (and my desktop machine died, I originally ordered a laptop with an intel card but this arrived instead an I couldn't get it exchanged). My desktop has had ATI cards for many years. First the r200 series as they had the best 3d driver for Linux, then I upgraded to an r600 a couple of months ago. That was kind of a mistake, I thought it was well supported but with a bit of waiting it is now becoming so.

Going back to the nvidia nightmare has been hard. I can pick between well functioning secondary screen functionality or accelerated X which makes my HD content viewable. 

If I was to vote with my dollars, it would definitely be an ATI card. They are good value and supportive of Free Software. Anything r300-r500 will work very well today, r600-700 are coming, hopefully very soon. The first code dropped today, documentation to come shortly. I have high hopes that it won't be long till the entire lines is somewhat well supported.

---

### Post by ronacc on 2008-12-30
I have always used Nvidia cards because for a long time they worked best for linux , thankfuly the situation is changing with AMD/ATI opening up their drivers and my next card will probably be ATI and if it is I intend to let Nvidia know why .

---

### Post by Turboflame on 2008-12-30
I upgraded from a Nvidia 7600GT to an ATI HD3850 about 6 months ago and haven't had any real problems. The only issue I had was that I have to disable compiz fusion before running any 3D app (otherwise there's a lot of flickering). 

IDK what your price range is so it's hard to recommend a specific card.

---

### Post by ronacc on 2008-12-30
thanks for the offer , I'm not ready to leap yet , when I do it will be something "mid range" I don't game so I wont stress it much , I usually wait for something decent but not "bleeding edge" to go on sale .How does ATI play with twinview or what ever their equivelent is ? the box that will probably get a new card would be my mmpc with a samsung 22" lcd (1680x1050) on dvi output and 42" hdlcd tv (1024x768) on  the VGA output .

---

