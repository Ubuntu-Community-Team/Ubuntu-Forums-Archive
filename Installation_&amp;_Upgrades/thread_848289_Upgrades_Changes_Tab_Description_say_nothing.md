---
title: "Upgrades Changes Tab Description say nothing"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by jreinis on 2008-07-03
"The list of changes is not available yet.
Please try again later."

That I see each time I run Ubuntu team upgrades.
I do not understand if there is no any chamges why they send so named upgrades?

---

### Post by mvdberg112 on 2008-07-03
In which program do you receive this message? With which steps do you start it?
After which actions does this message occur?
If it is in Update Manger (System-> Administration-> Update Manger), and you select a package and then the two tabs in the bottom pane are Changes and Description. The changes to be shown in this tab come from the internet the moment the item is selected. For some packages, no overview of changes might have been made available to be shown here, hence a message that info is not available .

---

### Post by SkonesMickLoud on 2008-07-03
Try updating your package list with the command:

```
sudo aptitude update
```

And then running the upgrade with:

```
sudo aptitude safe-upgrade
```

You can also run these commands as one:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

