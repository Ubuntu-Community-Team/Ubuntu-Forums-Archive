---
title: "Problem when installing google assistant on Ubuntu"
date: 2017-06-29
forum: Installation &amp; Upgrades
---

### Post by plopmon on 2017-06-29
I have recently switched to Ubuntu from Windows (because windows used to lag so much).  I had google assistant on Windows (using the SDK) and it was working perfectly fine. I used this tutorial [https://www.xda-developers.com/how-to-get-google-assistant-on-your-windows-mac-or-linux-machine/](https://www.xda-developers.com/how-to-get-google-assistant-on-your-windows-mac-or-linux-machine/) . im having all the credentials ready and all but when i execute this command [COLOR=#000000][FONT=monospace]python3 [/FONT][/COLOR][COLOR=#666600][FONT=monospace]-[/FONT][/COLOR][COLOR=#000000][FONT=monospace]m pip install google[/FONT][/COLOR][COLOR=#666600][FONT=monospace]-[/FONT][/COLOR][COLOR=#000000][FONT=monospace]assistant[/FONT][/COLOR][COLOR=#666600][FONT=monospace]-[/FONT][/COLOR][COLOR=#000000][FONT=monospace]sdk[/FONT][/COLOR][COLOR=#666600][FONT=monospace][[/FONT][/COLOR][COLOR=#000000][FONT=monospace]samples[/FONT][/COLOR][COLOR=#666600][FONT=monospace]]  terminal gives the following - /usr/bin/python3: No module named pip .

[/FONT][/COLOR]Can anyone help with this since i am new to linux

---

### Post by shridhar-kapshikar on 2017-06-30
Ubuntu 16.04 ships with both Python 3 and Python 2 pre-installed. To  make sure that our versions are up-to-date, let’s update and upgrade the  system with apt-get:
```

$ sudo apt-get update
$ sudo apt-get -y upgrade

```

Once the process is complete, we can check the version of Python 3 that is installed in the system by typing:
```

$ python3 -V

```

To manage software package for python, install pip3
```

$ sudo apt-get install -y python3-pip

```

Then in case of any package installation,
```

$ pip3 install <package_name>

``` 

Let me know in case of any questions.

---

