---
title: "Upgrading to 10.04 LTS from RC"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by bigredmachine878 on 2010-04-30
Hey guys, I've had the 10.04 installed on a notebook for about a week now and I want to upgrade to the LTS that was released today. When I go to check updates it shows me that everything is already updated. How can this be? Is there another way to upgrade from RC to LTS that I don't know about?
Thanks!

---

### Post by Bokonon on 2010-04-30
You should be 100% up and running.  I downloaded the distribution the day before and installed the updates.  

We both good to go (provided things are running smoothly for you).

FWIW, this has been the most painless update for me.  I only had to download anki separately and change my theme to a new one.  

Very nice work to the devel team.

---

### Post by carl4926 on 2010-04-30
I use aptitude
But you may already have updated without realising


```
sudo aptitude update

```
```
sudo aptitude full-upgrade
```

what do you get from:

```
cat /etc/lsb-release
```

---

### Post by bigredmachine878 on 2010-04-30
> **carl4926 said:**
> I use aptitude
But you may already have updated without realising


```
sudo aptitude update

``````
sudo aptitude full-upgrade
```what do you get from:

```
cat /etc/lsb-release
```

Says its 10.04 LTS..so I'm good then right? Does this mean I've been running the LTS version for a couple days now?

---

### Post by carl4926 on 2010-04-30
> **bigredmachine878 said:**
> Says its 10.04 LTS..so I'm good then right? Does this mean I've been running the LTS version for a couple days now?
I have. So yes, I guess so.:)

---

### Post by migs73 on 2010-04-30
Cool. I was wondering about that myself. I had read somewhere that the updates sorted it out but didn't know how to find out if it had (it had by the way). 10.04 running fine. Pat on back to the dev team.

---

