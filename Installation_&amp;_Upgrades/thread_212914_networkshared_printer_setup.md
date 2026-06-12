---
title: "network/shared printer setup"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-07-10
I had ask this before, but apparently from the answers I received, maybe my question was not understood, let me re-phrase my question.

In the printer setup facility in Ubuntu there are two main basic choices for setting up a printer, either as LOCAL or NETWORK.

I have a HP laserjet 2100 printer that I am connecting to one of my Ubuntu computers via parallel (LPT1), i.e. this printer has NO network card or network facility of any type.

If I want to be able to print to this same printer from my other three (3) Ubuntu computers which are on a hard wired Netgear hub, do I:

1) Set this printer up on the Ubuntu computer that it is physically attached to, as a **LOCAL** printer and then print to this printer from the other 3 computers via some sharing facility such as SAMBA or

2) Set this printer up on the Ubuntu computer that it is physically attached to, as a **NETWORK** printer and then print to this printer by setting up certain network printer parameters in the printer setup diagonal parameters on the computer that it is hooked directly to ?

To put it another way, how do I accomplish in Ubuntu what is commonly referred to in M/S windows as printer sharing ?

Thanks.

---

### Post by veki on 2006-07-29
You should put it as LOCAL on machine to which ti is attched to.

You have to put it as NETWROK nfrom other machines and write IP number of your machine on which it is attched to, so print task will go to that amchine and it will get it through the printer that is attched to that amchine.
OK?

veki

---

### Post by pecos.wil on 2006-08-05
along the lines of this problem, i have purchased a paralell port print server, i have setup my windows computers just fine, but i can't seem to find the right combination of setting to allow my LinBox [Ubuntu] to access the printer.

I have access via the web login and I know the "name" of the print server //Canoni550/P1. I have looked up the CUPS driver [BJC 8200].  So now what do I do?
](*,)

---

### Post by tarclee on 2006-08-28
the local printer that attach to the pc,should i make it as fix ip?

---

