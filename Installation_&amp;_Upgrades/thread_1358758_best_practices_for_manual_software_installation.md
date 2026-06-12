---
title: "best practices for manual software installation"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by ricoPan on 2009-12-18
Moving to my own ubuntu machine from an academic fedora setting where I didn't have root priv.  So far installation for this scientific workstation has been a great experience.  Now I am running into issues regarding custom package installation, and though I have a work around, I would like to know if there is a better way.

The specifics should not matter much -- but here they are.  I use python, and in my case, having numpy built with custom tuned linear algebra libraries (Lapack) is necessary.  This means I must build the numpy dependency ATLAS and tune myself, as the ubuntu numpy, as I understand it, will not use my custom ATLAS.  Did this without issue, and installed numpy manually.  Uses ATLAS tuned threaded libraries.

Next I wanted to install another python package, matplotlib, which requires numpy.  The problem is that matplotlib has a bunch of other dependencies, and I want to use apt-get.  But apt-get wants the starndard ubuntu python-numpy, which is both an older version than mine and also will not use my tuned ATLAS.

I assume I can install matplotlib with apt-get without overwriting my numpy, but I haven't figured out how.  I learned about checkinstall to maintain my manual installations, which seems to work, apt-get, aptitude, and synaptic all are aware of my numpy if I use checkinstall.  Great!

I also read that I can use aptitude 'hold' or 'pin' with apt-get, or 'lock' with synaptic  to automatic upgrading.   However, if I use apt-get or aptitude to install software (eg matplotlib) that needs my manual installation (eg numpy), it continues to overwrite my version, regardless of these holds, pins, locks.  Am I failing to do something, or is this expected behavior?

As it is, it seems that once I depart from aptitude /apt-get, I can't easily return to using it, even with checkinstall, as I run the constant risk of overwriting my manual installations.  Is this correct?  In this example, I can still use aptitude to install each of matplotlib dependencies one by one, avoiding numpy, which is certainly helpful but perhaps more time consuming than need be, and then install matplotlib manually.  That works.

Is there a way of telling apt-get /aptitude that my numpy is adequate for matplotlib, and to quit complaining and just use it and never overwrite?  Or must I now always be on the look out for installations that will sneak in a numpy overwrite?  What are best practices here?

This is what happens when everything is so convenient -- now I want it all.

---

### Post by lloyd_b on 2009-12-19
> **ricoPan said:**
> Moving to my own ubuntu machine from an academic fedora setting where I didn't have root priv.  So far installation for this scientific workstation has been a great experience.  Now I am running into issues regarding custom package installation, and though I have a work around, I would like to know if there is a better way.

The specifics should not matter much -- but here they are.  I use python, and in my case, having numpy built with custom tuned linear algebra libraries (Lapack) is necessary.  This means I must build the numpy dependency ATLAS and tune myself, as the ubuntu numpy, as I understand it, will not use my custom ATLAS.  Did this without issue, and installed numpy manually.  Uses ATLAS tuned threaded libraries.

Next I wanted to install another python package, matplotlib, which requires numpy.  The problem is that matplotlib has a bunch of other dependencies, and I want to use apt-get.  But apt-get wants the starndard ubuntu python-numpy, which is both an older version than mine and also will not use my tuned ATLAS.

I assume I can install matplotlib with apt-get without overwriting my numpy, but I haven't figured out how.  I learned about checkinstall to maintain my manual installations, which seems to work, apt-get, aptitude, and synaptic all are aware of my numpy if I use checkinstall.  Great!

I also read that I can use aptitude 'hold' or 'pin' with apt-get, or 'lock' with synaptic  to automatic upgrading.   However, if I use apt-get or aptitude to install software (eg matplotlib) that needs my manual installation (eg numpy), it continues to overwrite my version, regardless of these holds, pins, locks.  Am I failing to do something, or is this expected behavior?

As it is, it seems that once I depart from aptitude /apt-get, I can't easily return to using it, even with checkinstall, as I run the constant risk of overwriting my manual installations.  Is this correct?  In this example, I can still use aptitude to install each of matplotlib dependencies one by one, avoiding numpy, which is certainly helpful but perhaps more time consuming than need be, and then install matplotlib manually.  That works.

Is there a way of telling apt-get /aptitude that my numpy is adequate for matplotlib, and to quit complaining and just use it and never overwrite?  Or must I now always be on the look out for installations that will sneak in a numpy overwrite?  What are best practices here?

This is what happens when everything is so convenient -- now I want it all.

First question: *where* did you install your custom software?  If you installed into the "/usr" tree ("/usr/bin", "/usr/lib", etc) then you're going to get conflicts.

Best practice is to install custom versions of software to "/usr/local" rather then "/usr".  This will allow you to have both the standard version and your custom version installed.  You may have to play with the LD_LIBRARY_PATH environment variable in order to get it to use your custom version rather than the default version, though.

Lloyd B.

---

### Post by ricoPan on 2009-12-20
Thanks lloyd_b for the response.  Yes, I am using /usr/local as you suggest.

Any ideas about preventing aptitude or apt-get from overwriting my software?  From what I gathered, using apptitude hold <package_name> should prevent an automatic upgrade, but it does not prevent it from installing over it as a dependency for new software.  Maybe I'm not using apptitude correctly?

Thanks,
Rich

---

### Post by ricoPan on 2009-12-26
To update: it seems this is a problem that has no general solution.  For python, however, I have discovered virtualenv, and virtualenvwrapper, that support multiple installations of python and python packages either entirely separate or using packages from the standard installation.  That works for me -- allowing aptitude to control upgrading standard python, but keeping control of separate numpy in a virtualenv.

In ubuntu's favor I'll say that in some late night thrashing about from a remote computer in order to update the system python to my needs, I managed to trigger a cascading delete of the gnome desktop.  Ubuntu was robust enough to right itself and reinstall gnome while still running, though did need one reboot.

---

