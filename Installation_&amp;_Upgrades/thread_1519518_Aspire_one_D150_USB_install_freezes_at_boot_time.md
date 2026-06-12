---
title: "Aspire one D150 USB install freezes at boot time"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by Capslock118 on 2010-06-28
Hello there,

I am trying to install ubuntu netbook edition on my Acer aspire one D150.

I have tried to do this before with version 9 with no luck so I waited until 10 to see if the problem goes away; appearently it has not.

I put the ubuntu install files onto a USB stick [according to the instructions from ubuntu here]("http://www.ubuntu.com/netbook/get-ubuntu/download") for windows (I have windows xp on the netbook now).

When I shut the PC down and turn it back on with the USB key inserted, the laptop just seems to hang at the ACER splashscreen. This screen is where I could press F2 for setup or F12 for boot order; the buttons do not respond, the USB key appears inactive. Again, it just seems to hang.

I've waited for as long as letting it run all night to see if it goes anywhere by the morning with no luck.

Whats the deal here, anyone know or could direct me to the right place? I can't seem to find via google search or forums search anyone with this exact problem.

---

### Post by Capslock118 on 2010-06-28
Hello again,

I just realized that I probably should disable the 'quick boot' i.e. the acer splash screen so that I could see what stage the machine freezes on at boot time.


It turns out that it seems that the laptop gets to the point of identifying the CPU, but freezes when trying to identify the hard drive.

I am not sure if it actually cannot find the hard drive or if there is a conflict when the USB key is installed. Essentially it is fact for my PC that this freeze only happens when inserting the USB key.

The USB key is a staples brand 2gb.

Any thoughts? I'd really like to start using ubuntu again; this is a terrific internet community

---

### Post by Capslock118 on 2010-06-30
Last night I tried to install ubuntu netbook remix 10.04 using the wubi installer instead and I had absolutely no problems; it worked like a charm.

I have a problem with this though; I don't want to dual boot. If anything, I would put windows on a virtual machine if I ended up needing it but I know from past experience I would have no use for dual boot.

Further, I like partitioning my hard drive in this way:
Partition one: in the 'front' of the drive, small partition used only to install the operating system and applications

Partition two: swap (though I might use an SD card for this with my netbook, not sure).

Parition three: store VMs, databases, and code from various projects I undertake.

Partition four: store photos, videos, games, etc. This is the largest partition


That said I really want to get passed this problem I am having.


I tried flashing the bios to the latest version acer had on their website but it didnt help any.

I am starting to wonder if maybe the USB key, but I have no idea what to test.

---

