---
title: "Upgrade Pending- Only way to Meerkat"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by seanbw on 2011-02-07
I am on Lynx 32 and have learned to manage my Ubuntu to such a level that it is the only OS I use.I am now happy to upgrade to Meerkat but only if I can resolve two particular issues. No 1 is Virtualbox (Oracle version) - I discovered that OOO - Word did not satisfy me on the proposal I needed to write. The references just did not work as I use endnote (not footnote) and OOO just screwed it up each time. So I reinstalled my Vista in Virtualbox, then MS Office and found it worked. In fact it worked so well that I am now happily plugging away on MS Word on my proposal in Windows. 
Then I installed MS Office on Wine and although the wine menu did not work, I can start Word on Linux by clicking on the proposal written in word so now I have two ways of working on my proposal. In addition, I have Android x86 installed on Virtualbox as well as Mendeley, Opera, Bible software (Wiindows only) and IE8. 
On Linux, I have Mendeley, Opera, Sigil, Picassa and Calibre installed and all working to my satisfaction so I am able to move information between Linux and Windows.
As a result of this, I have not upgraded to Meerkat and won't be able to unless I find a way of moving my Virtualboc/Windows installation. 
No 2 is: I know I can upgrade Lynx to Meerkat but on my current Lynx I have the option of using Ubuntu or Kubuntu but in order to save space, I would like to upgrade to Kubuntu alone.
My questions are: 
[LIST=1]
[*]Is it possible to move my programs - Virtualbox/Windows & Androidx86 to Meerkat? If yes, how.
[*]If not, am I stuck with upgrading and If I am, will my programs survive?
[*]If I have to upgrade, can I upgrade to just Kubuntu or must I upgrade to both flavours? 
[*]Finally can I upgrade from Lynx 32 to Meerkat 64? Is it an option?
[/LIST]
Thank you.

---

### Post by seanbw on 2011-02-07
Many thanks for viewing and responding - I hope. Slumberland beckons. bedtime was 4 hours ago. Yeeah I know - slow writer - brain faster than puny finger. snore.... snore... snore.... Good Night and Thanks once again.

---

### Post by nuffink666 on 2011-03-07
answer to some of the questions

1) From your post if your running Android Windows etc in the virtualbox app then porting to meerkat is no problem, i run meerkat with virtualbox 4.0.4 (latest ATOW) and works fine, if for any reason virtualbox complains on the UUID of the disks you can regenrate a new uuid via the VBoxManage internalcommnads sethduid. if upgrading then just upgrade virtualbox if necessary, if installing meerkat then just save off the vdi disks or wotever format and recreate VM with existing disks after upgrade.
2) they should and if you can upgrade is obv better as you wont have to reinstall any of your current apps that arent part of the meerkat package, the vm apps will obv be fine as they in a vm
3) Dunno
4) You cant upgrade from 32 bit to 64 you would have to install 64 bit version and then upgrade but in that case just install 64 bit, basically there is no upgrade path for different bit versions

Think i have understood your requests?

---

### Post by seanbw on 2011-03-07
Many thanks for this response. It appears that I have to install to move from 32 bit to 64 bit. Since the only problem I  have is my Windows Vista running in Oracle Virtualbox and the danger I face in not having it registered by Microsoft a third time, this is my only hesitation point. I was thinking of backing the vdi files in lynx/virtualbox and restoring it in meerkat/virtualbox.
May try that first. I am very proud of being able to installing and running Vista /MS Office 2007 on virtualbox whilst being on Lynx all the time without having to bother with all these silly viruses and associated windows problems (especially with a 14 yr old son who does not think 2ce with downloading files from the net)
I really must try to backup and restore first otherwise its the upgrade path for me.
Once again thanks.

Yes you understood my requests perfectly.

---

