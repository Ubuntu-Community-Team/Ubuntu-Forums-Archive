---
title: "Ubuntu on new Dell Studio 15"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Rackstar on 2010-05-06
Hey,

I'm really thinking of buying this laptop:

[http://www1.euro.dell.com/be/nl/thuis/Laptops/laptop-studio-1555/pd.aspx?refid=laptop-studio-1555&s=dhs&cs=bedhs1&~ck=mn](http://www1.euro.dell.com/be/nl/thuis/Laptops/laptop-studio-1555/pd.aspx?refid=laptop-studio-1555&s=dhs&cs=bedhs1&~ck=mn)

But I'm doubting if I would take the i7 processor or not... My question is: does quad core become more or less hot than dual core?

More processors, but less powerfull or two strong ones?

And ATI Mobility Radeon™ HD5470, I heard there could be some trouble with this graphics card on Ubuntu 10.04? I don't mind fixing things, but is it fixable?

Does anyone have this laptop?

Some comments would be hugely appreciated :)
Thanks!

---

### Post by clevertomato on 2010-05-07
I cannot comment on exact hardware but I have a Dell Studio 1555 with ATI Mobility Radeon HD 4570. It works flawlessly with Karmic but I can't get video drivers to work perfectly in Lucid.

Also, I'm no expert, but unless you have plans to run specific software that will take advantage of them, I'm not sure having 4 cores will really benefit you much.

---

### Post by Rackstar on 2010-05-07
Thanks for the comment!

This isn't such a reinsurance :D

I've never had an ATI card before, always been happy with NVidia, only the lack for auto-detecting second screen was bugging me.

How is the state of the open source driver? Is it acceptable or shouldn't I count on that?

Thanks!

---

### Post by dino99 on 2010-05-07
Dell is more "closed" than "opened", read forums about Dell issues, better to buy something else (acer or ...)

More issues with Ati too and higher temperatures

ubuntu nvidia drivers works well with multi screens

---

### Post by mervinb on 2010-05-07
I don't have the latest Studio 15, but an older Dell Studio 15 1537.

- I was previously using the AMD fglrx driver on Karmic and earlier because I had suspend/resume issues on the open source 'ati' driver. I now use the ati driver, and hibernate works well. Suspend is not functional (see next).
- Suspend/resume in earlier alphas of Lucid caused the fan not to resume. Some time in the test cycle, I noticed that suspend was disabled, and I recall reading that this was to prevent the overheating issue (related to Radeon graphics). Resume after hibernate is fine, with the fan resuming, perhaps too strongly.
- Since beta, Lucid has been extremely stable with my Studio 15

No guarantees for your latest Studio 15 model, but Lucid has been a step up in stability and (2D) graphics performance for me compared to Hardy/Karmic.

---

### Post by Rackstar on 2010-05-07
> **dino99 said:**
> Dell is more "closed" than "opened", read forums about Dell issues, better to buy something else (acer or ...)

More issues with Ati too and higher temperatures

ubuntu nvidia drivers works well with multi screens

Do newer NVidia cards support this?

- Connect cable external monitor
- Voila!

I hate it with my current laptop:

- Connect
- Open Nvidia Settings
- Detect screens
- Configure screens
- Apply
- "Do you want to keep these settings?" - Yes
- Close
- And still fail to set the primary screen correctly

Not really happy with my Acer, especially the support was awful (had to wait a month till I got my laptop back, with only the cable between screen and motherboard replaced)

It would be nice if I could go and test one.. But that doesn't seem that possible.

I'm always a little cautious when reading about problems with laptops on forums, because mostly only people with problems tend to post.

I thought Dell was a good choice, as in Belgium next month, they are going to sell with Ubuntu.

---

### Post by Rackstar on 2010-05-07
> **mervinb said:**
> 
- Since beta, Lucid has been extremely stable with my Studio 15

No guarantees for your latest Studio 15 model, but Lucid has been a step up in stability and (2D) graphics performance for me compared to Hardy/Karmic.

I'm not a gamer, so good 2D performance is the major thing. But you are able to use compiz and such?

---

