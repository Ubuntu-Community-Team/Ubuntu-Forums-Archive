---
title: "Fixing Meta-Release Problem on Feisty -&gt; Gutsy Upgrade"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by uwflatlander on 2007-09-24
These are partially for my own notes, but also to help others. This guide is to help folks who are having problems with the upgrade process when it complains about problems in the meta-release file.

The normal upgrade method to get to from Feisty to Gutsy is first to update your Feisty system to the latest and greatest.

```

# sudo apt-get update
# sudo apt-get upgrade
```

That should give you all the latest Feisty packages. Next, run the upgrade.

```

# sudo update-manager -c -d
```

This should popup the update manager. In the manager, there will be a notice about a new version available. 

If you see that notice, **wonderful!** You can stop reading. :)

If you do not see that notice, chances are you might see this notice in the console after starting up the Update Manager:

```

current dist not found in meta-release file
```

There is some problem in the Update Manager that is deleting the contents of the meta-release file. This file is what the Update Manager needs in order figure out what release is currently installed and  what are the newer releases available. Since the Update Manager is deleting this file, it doesn't have a clue how to do the upgrade. So what we need to do is replace the file it deleted.

Close the Update Manager and run this command.

```

# sudo wget http://changelogs.ubuntu.com/meta-release-development -O /var/lib/update-manager/meta-release
```

This will refresh the meta-release file with the Gutsy development release info. Now run the update manager again.

```

# sudo update-manager -c -d
```

Now you should see the notice about a new version being available. You can now upgrade and have fun testing out Gutsy.

if this doesn't solve your problem, let me know and I will try to lend a hand.

---

### Post by jruschme on 2007-09-25
Thanks... just what the doctor ordered.

---

