---
title: "Partition Scheme - Suggestion"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by gdatuk on 2010-04-09
Hi,

I am a total noob for Linux / Ubuntu. I have been using windows all my life and I decided to get rid of Bill finally. I want to install Ubuntu by Manually partitioning my HD.

I have a 500GB HDD.

Please suggest me an optimal partition scheme. I repeat i am a total Noob. please let me know details for each partition like 
1. Primary or Logical
2. type
3. mount point
4. size

I am having no other OS in the pc. just planning to have ubuntu. no dual boot needed.

---

### Post by engine on 2010-04-10
I'll watch your thread with interest, as I have very nearly the same question <g> I found some information somewhere (you know what the web's like ...] on an ubuntu page, made notes, and never found the page again :-{

I'm thinking of using the following settings for a 200Gb disk: can anyone out there advise me whether they are reasonable? and advise gdatuk whether he/she can simply rescale for a larger disk? Thanks in advance!

```

partition           Mb   mount point
/dev/sda1      4694.24   /
/dev/sda10   204332.4    /home
/dev/sda6      7226.79   /usr
/dev/sda7      4879.62   /var
/dev/sda8      4802.39   /opt
/dev/sda9      6825.28   /tmp

```

---

### Post by beta.tester on 2010-04-10
> **gdatuk said:**
> Hi,

I am a total noob for Linux / Ubuntu. I have been using windows all my life and I decided to get rid of Bill finally. I want to install Ubuntu by Manually partitioning my HD.

I have a 500GB HDD.

Please suggest me an optimal partition scheme. I repeat i am a total Noob. please let me know details for each partition like 
1. Primary or Logical
2. type
3. mount point
4. size

I am having no other OS in the pc. just planning to have ubuntu. no dual boot needed.

Hi

Just my opinion :)

You also need a /swap partition, if I were you I would simply have:

root / upto 100G
home /home the remainder after /root and swap created :)
swap swap    5G

That is it simplistically and the only 3 partitions I have here on my Linux HDD :)

kind regards and keep on ubunuting    john

---

