---
title: "unable to install from software center"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by manojtm on 2012-07-19
I have installed ubuntu 11.04 and also installed few software from Ubuntu Software Center. I was installing Google-talk and i aborted the download in the middle. But after that, i am un able to install any other software from the center, when i choose any, it says to REPAIR google-talk. When i click on REPAIR it end up with error. And even i came up with a red icon in system try which has " Error;brokencout>o". I used command - "apt-get install --fix-broken" it downloads few packages but the error still sucks. How can i over come from these two

---

### Post by kc1di on 2012-07-19
Hi manojtm, 
Welcome to Ubuntu and sorry your having problems. 

I think this will fix it though
go to a terminal and type the following commands one at a time:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

then try your software center again. 

P.S. I would install synaptic package manager and use that.

good Luck ,
Dave

---

### Post by raja.genupula on 2012-07-19
> **kc1di said:**
> Hi manojtm, 
Welcome to Ubuntu and sorry your having problems. 

I think this will fix it though
go to a terminal and type the following commands one at a time:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

then try your software center again. 

P.S. I would install synaptic package manager and use that.

good Luck ,
Dave

Hi My friend this is not the solution going to work .this is wrong answer .

@OP open your terminal and type this 

```
sudo apt-get install -f

```

paste here the output of terminal after the command .

thank you .

---

