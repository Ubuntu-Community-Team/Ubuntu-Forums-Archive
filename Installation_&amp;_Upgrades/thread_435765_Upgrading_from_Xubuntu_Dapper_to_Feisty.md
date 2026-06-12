---
title: "Upgrading from Xubuntu Dapper to Feisty"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by Apoorv on 2007-05-07
OK, no nonsense, cut short explanation. HOW DO I DO IT? For Xubuntu 6.06, I'm ready to do anything, ANYTHING. I know that I'll first have to upgrade to Edgy, and then Feisty, but I want a cut down, brief explanation.

This doesn't work for Xubuntu -
```
$ gksu "update-manager -c"
```

A request to the mods :
[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)
I went through this topic, but I found it very difficult to find info applicable to me. I request the mods not to make stickies like these, instead, let these topics be open for discussion, and when a stable tested solution is achieved, then include it in a locked sticky which only mods can edit. This way we have a few posts in a sticky thread which contain just the main content of the whole discussion of the forum.

---

### Post by bapoumba on 2007-05-07
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/update-manager/+bug/68027](https://launchpad.net/ubuntu/+source/update-manager/+bug/68027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello :)
Do you have a separate /home partition? An alternative solution could be to make a clean feisty install.
In the above mentioned thread, [post #2]("http://ubuntuforums.org/showpost.php?p=1675599&postcount=2") links to a bug report.

---

### Post by jis on 2007-05-08
Do you mean sectioin "Clean install with /home on separate partition" at [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion?](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion?) How exactly that can be applied for _Xubuntu_? Could you use either alternate or desktop CD?

---

### Post by Topsiho on 2007-05-08
The answers to your questions are yes, if you use an Xubuntu CD instead of Ubuntu or Kubuntu. I write this having no experience with Xubuntu, but as far as I know there is no reason why Xubuntu should be different.

The important thing is NOT to format your separate /home partition and to set the mount points correctly.

This is also why it's wise to have a separate /home partition.

If the Live CD doesn't work you could try the alternate CD: on some computers the bootprocedure on the Live CD of Feisty sucks, I now think because of timing problems with some parallel boot processes.

Topsiho

---

