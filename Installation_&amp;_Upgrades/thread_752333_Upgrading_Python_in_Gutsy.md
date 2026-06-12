---
title: "Upgrading Python in Gutsy"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by ibmg on 2008-04-11
Hi all,

In a moment's folly, I decided to upgrade my Python 2.5.1 (default in Gutsy) to 2.5.2 thinking that since it wasn't a major version everything would be ok.

However installing 2.5.2 from source, although successful, caused an even larger problem. Now my system is partially FUBAR, especially with things related to python and GTK. Almost none of my installed python libraries work and need to be recompiled and reinstalled from source. Reinstalling the libraries (and Python2.5) from repositories did not work.

I basically have 2 questions.

1) What is the "correct" way to upgrade Python assuming the repositories do not have the latest version

2) How can i revert back to the Python version in the repositories (i.e. 2.5.1)

---

### Post by ajgreeny on 2008-04-11
I don't know what would happen if you used **synaptic** and **force version** from the Package menu to downgrade python, but it could be worth trying.  I suspect there could be a load of dependencies that may upset that as a possibility, but maybe, just maybe---?

---

### Post by ibmg on 2008-04-11
Hi ajgreen,

I tried that but version still remains as 2.5.2 after reinstallation

---

