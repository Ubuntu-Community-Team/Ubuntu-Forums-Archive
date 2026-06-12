---
title: "Rubygems problem"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by EvanR on 2008-06-11
Hi, i've installed ubuntu 8.04 and am loving it. The only problem i have is with rubygems. I've done

sudo apt-get install rubygems

Then i ran the gem update so im using rubygems1.1.1 now. If i install rails using, sudo gem install rails -y, then everything works fine except if i try to run a rails command in the terminal i get an error!

Example:

```

/home/evan/rails_apps# rails my_app
The program 'rails' is currently not installed.  You can install it by typing:
apt-get install rails
bash: rails: command not found

```

---

### Post by mxg01 on 2008-06-11
You've installed the rails gem. To use it you reference it in your Ruby code:

```
require 'rails'
```

If you want to run rails from the command line then you'll need to do as it suggests and:

```
sudo apt-get install rails
```

---

### Post by EvanR on 2008-06-11
Yes, that is the obvious solution but i thought that it wasn't a good idea to switch between gem install and sudo apt-get install?

Anyways i've fixed this by removed the outdated rubygems from aptitude.

---

