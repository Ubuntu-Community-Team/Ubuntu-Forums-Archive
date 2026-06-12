---
title: "Unable to install php5-ffmpeg"
date: 2016-06-06
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2016-06-06
Hello,

I am trying to install the php5-ffmpeg and I've got the below error:

```

# sudo apt-get install php5-ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 php5-ffmpeg : Depends: phpapi-20090626
E: Unable to correct problems, you have held broken packages.

```


and I tried to install the tar package:

```

configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for ffmpeg support... yes, shared
checking whether to force gd support in ffmpeg-php... no
checking for ffmpeg headers... ...found in /usr/include/libavcodec
checking for ffmpeg libavcodec.so... 
configure: error: ffmpeg shared libraries not found. Make sure ffmpeg is compiled as shared libraries using the --enable-shared option

```


Thanks in advance

---

### Post by FakeOutdoorsman on 2016-06-07
You didn't mention your Ubuntu version.

Are you sure you even need a PHP wrapper for ffmpeg? Especially one that has been dead since 2007.
[https://trac.ffmpeg.org/wiki/PHP](https://trac.ffmpeg.org/wiki/PHP)

---

### Post by alfirdaous on 2016-06-08
well I changed it with getID3, but before that, I faced this while installing the php5-ffmpeg:

```

# phpize
Configuring for:
PHP Api Version:         20121113
Zend Module Api No:      20121212
Zend Extension Api No:   220121212
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LC_CTYPE = "UTF-8",
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LC_CTYPE = "UTF-8",
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

---

