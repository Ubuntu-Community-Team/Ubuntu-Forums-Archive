---
title: "RPi GPIO Library on Ubuntu Snappy Core"
date: 2018-08-21
forum: Installation &amp; Upgrades
---

### Post by xav38 on 2018-08-21
Hello,

I started to play with ubuntu core to make a simple monitoring tools. To comply with my poor level and lack of time for developping it, I would like to run Node-Red on Ubuntu Core (that's working), the problem is I can't install the RPi GPIO library to access to them via Node-Red.
I installed the Classic Snap to run those commands :

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install python-pip python-dev
sudo pip install RPi.GPIO 
``` 

Everything run smoothly except the last one. When I running it, I'm stuck with that :


```
Collecting RPi.GPIO
  Downloading [https://files.pythonhosted.org/packages/e2/58/6e1b775606da6439fa3fd1550e7f714ac62aa75e162eed29dbec684ecb3e/RPi.GPIO-0.6.3.tar.gz](https://files.pythonhosted.org/packages/e2/58/6e1b775606da6439fa3fd1550e7f714ac62aa75e162eed29dbec684ecb3e/RPi.GPIO-0.6.3.tar.gz)
Installing collected packages: RPi.GPIO
  Running setup.py install for RPi.GPIO ... error
    Complete output from command /usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-QRZKqJ/RPi.GPIO/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --record /tmp/pip-OqtqFt-record/install-record.txt --single-version-externally-managed --compile:
    running install
    running build
    running build_py
    creating build
    creating build/lib.linux-armv7l-2.7
    creating build/lib.linux-armv7l-2.7/RPi
    copying RPi/__init__.py -> build/lib.linux-armv7l-2.7/RPi
    creating build/lib.linux-armv7l-2.7/RPi/GPIO
    copying RPi/GPIO/__init__.py -> build/lib.linux-armv7l-2.7/RPi/GPIO
    running build_ext
    building 'RPi._GPIO' extension
    creating build/temp.linux-armv7l-2.7
    creating build/temp.linux-armv7l-2.7/source
    arm-linux-gnueabihf-gcc -pthread -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fno-strict-aliasing -Wdate-time -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security -fPIC -I/usr/include/python2.7 -c source/py_gpio.c -o build/temp.linux-armv7l-2.7/source/py_gpio.o
    unable to execute 'arm-linux-gnueabihf-gcc': No such file or directory
    error: command 'arm-linux-gnueabihf-gcc' failed with exit status 1
```

Unfortunately, google seems not to be my friend on that, so I'm turning on the community.

Thanks by advance.

Xavier.

---

### Post by QIII on 2018-08-22
Hello!

Please use code tags to enclose terminal commands and messages.  That preserves formatting and makes your posts easier to read.

To use code tags, either:

1.  Click the # button above the text entry box, place your cursor between the code tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following it.  The square brackets are required.

Cheers!

---

