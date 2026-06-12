---
title: "Upgrade to Feisty - Repository Problems"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by glenm on 2007-05-07
I'm trying to upgrade from Edgy to Feisty using the distribution upgrade tool.

I get this message "Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)"

That repository was removed from the sources list some time ago.  When I use Adept -> Manage Repositories the wine.budgetdedicated.com repository is  not in the list.  When I click on Fetch Updates in Adept this repository is stil being accessed. 

As far as I know I haven't got any packages installed from that repository I removed them all ( or so I thought )

How can I find out where this reference to the wine reposity is so I can remove it?

---

### Post by melissawm on 2007-05-07
Did you try doing

```
sudo apt-get update
```

in a terminal BEFORE using adept?

If not, try it. If it still doesn't work, try checking your /etc/apt/sources.list from the terminal :

```
sudo gedit /etc/apt/sources.list 
```

in Ubuntu or

```
 sudo kate /etc/apt/sources.list 
```

in Kubuntu. If there is a line about this repository, delete it, save the alterations in this file, and repeat "sudo apt-get update". Hope it helps...

---

### Post by glenm on 2007-05-08
Thanks - I tried the apt-get update and editing the sources.list as you suggested but it still doesn't work

When I edit /etc/apt/sources.list the wine repository isn't listed in there.

When I do an apt-get update the wine repository is queried.  The list of repositories that apt queries must depend on sources.list and something else.

How would I find out if I have a package still installed from the wine repository?

---

