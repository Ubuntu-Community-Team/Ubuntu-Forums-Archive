---
title: "upgrading from hardy to 8.10 beta with alternate cd"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by quizzelsnatch on 2008-10-06
I'm trying to upgrade my existing installation through the alternate cd by mounting the iso and then running "kdesu "sh /cdrom/cdromupgrade" in the terminal. After it asks me if I want to download or use the updates on the cd, the program exits out. This is what the terminal says:

helios@olympus:~$ kdesu "sh /cdrom/cdromupgrade"
passprompt

adept_manager: no process killed

adept_updater: no process killed

can't load DistUpgradeViewGtk (No module named vte)
exitMainLoop

Error in sys.excepthook:
Traceback (most recent call last):
  File "/tmp/tmp.coRmA12467/DistUpgradeViewKDE.py", line 568, in _handleException

    self.translate_widget_children(self.dialog)

AttributeError: 'DistUpgradeViewKDE' object has no attribute 'dialog'

Original exception was:
Traceback (most recent call last):
  File "/tmp/tmp.coRmA12467/intrepid", line 76, in <module>

    app.run()
  File "/tmp/tmp.coRmA12467/DistUpgradeController.py", line 1502, in run

    self.fullUpgrade()

  File "/tmp/tmp.coRmA12467/DistUpgradeController.py", line 1421, in fullUpgrade

    if not self.doPostInitialUpdate():

  File "/tmp/tmp.coRmA12467/DistUpgradeController.py", line 652, in doPostInitialUpdate

    self.quirks.run("PostInitialUpdate")

  File "/tmp/tmp.coRmA12467/DistUpgradeQuirks.py", line 61, in run
    func()
  File "/tmp/tmp.coRmA12467/DistUpgradeQuirks.py", line 98, in intrepidPostInitialUpdate

    res = self._view.askYesNoQuestion(_("Upgrading may reduce desktop "
NameError: global name '_' is not defined

I am currently running KDE 4.1.2, everything is upgraded to the latest, also, I installed ubuntu through the minimal-cli cd and installed only the specific packages I wanted for a KDE 4.1 desktop (i'm thinking this might be where my problem lies, I may be missing a package needed).

---

### Post by dath1974 on 2008-10-08
I am seeing the same problem while trying to upgrade from the network.  It looks like this is a bug with the DistUpgradeQuirks.py script not correctly prompting for a response when you are running the fglrx driver (which isn't compatible with the new version of X that comes with 8.10, so therefore you must be migrated to the opensource driver).  I'm going to try manually "downgrading" myself to the opensource driver before the update and then try again as I'm not very familiar with the updating process and don't want to bother hacking/fixing the scripts.

You'll want to be very careful here as your video card may or may not work well with the opensource driver (assuming you're really seeing the same issue I am), depending upon which particular chipset you have.  I have a Mobility X1300, which is reported to work with the latest opensource driver, though with limited 3d support. . .  Best to check carefully before you trudge on ahead!

---

### Post by quizzelsnatch on 2008-10-08
I am using the x1800xt, which I *think* is supported by the radeonhd driver. Not sure though, I'll just wait, it's only the beta anyways.

---

