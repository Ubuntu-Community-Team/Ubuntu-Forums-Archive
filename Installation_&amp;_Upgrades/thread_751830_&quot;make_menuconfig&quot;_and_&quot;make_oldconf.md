---
title: "&quot;make menuconfig&quot; and &quot;make oldconfig&quot; disrespect .config"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by mondalaci on 2008-04-10
I try to build a customized kernel using the official Ubuntu .config file.

```
cd /usr/src
wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.14.tar.bz2
tar xjvvf linux-2.6.22.14.tar.bz2
cd linux-2.6.22.14
cp /boot/config-2.6.22-14-generic .
make menuconfig
[CHANGE NOTHING, SAVE THE CONFIGURATION]
```

The resulting .config file that I got is the same
* whether I copy the official Ubuntu config file to the kernel dir or not
* whether I explicitly load .config inside menuconfig
* whether I use "make oldconfig" instead of "make menuconfig"

So my experience is that .config gets utterly disrespected.

I am doing something wrong?

Thanks in advance!

---

### Post by IntuitiveNipple on 2008-04-17
You need to correctly name the file to **.config**:
```

cd /usr/src/linux-2.6.22.14
cp /boot/config-2.6.22-14-generic ./.config
make menuconfig

```
See my [Custom Build guides and scripts](http://tjworld.net/wiki/Linux/Ubuntu/Kernel/CustomBuild)

---

### Post by mondalaci on 2008-04-18
I meant copying the config file as .config, but it doesn't work.  I get identical files as the end result either way.  Do you have any ideas?

---

### Post by mondalaci on 2008-05-04
I did some investigation and it seems to me that the Ubuntu .config file and the default mainstream kernel .config file configuration directives are identical.  I thought this is statiscically impossible, but this seems to be the case.

I've written a Python script to test it:

```
#!/usr/bin/env python

import sys

def make_config_dict(filename):
    config_dict = {}
    for line in open(filename):
        line = line.strip()
        if len(line) > 0 and line[0] != '#':
            fields = line.split('=')
            if len(fields) != 2:
                print 'errorneous line: "%s"' % (line)
                continue
            (name, value) = fields
            config_dict[name] = value
    return config_dict

def detect_conflicts(filename1, filename2):
    config_dict1 = make_config_dict(filename1)
    config_dict2 = make_config_dict(filename2)
    for config_directive in config_dict1.keys():
        if config_dict2.has_key(config_directive) and \
           config_dict1[config_directive] != config_dict2[config_directive]:
            print 'directive "%s" value mismatch: "%s" | "%s"' % \
            (config_directive, config_dict1[config_directive], config_dict2[config_directive])

if __name__ == '__main__':
    if len(sys.argv) != 3:
        print 'Usage detect-conflicts .config1 .config2'
        sys.exit()
    detect_conflicts(sys.argv[1], sys.argv[2])

```

Running "detect-conflicts.py .config.ubuntu .config" after running "make menuconfig" doesn't report me any differences.  (I've tested it with different configurations and it reported the differing configuration directives correctly.)

Well, this explains pretty well why I get identical configuration files using "make menuconfig" with or without the default Ubuntu .config file.

End of story.

---

