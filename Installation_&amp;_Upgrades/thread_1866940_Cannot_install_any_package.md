---
title: "Cannot install any package"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by dwit.udeshi on 2011-10-22
I am new to ubuntu and am using ubuntu 11.04 (64-bit) but i 
cannot install any downloaded software packages using ubuntu software center. I cannot event istall any updates by update manager. following error message is displayed. Please help me!

installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
 Extracting templates from packages: 11%% Extracting templates from packages: 23%% Extracting templates from packages: 35%% Extracting templates from packages: 47%% Extracting templates from packages: 59%% Extracting templates from packages: 71%% Extracting templates from packages: 83%% Extracting templates from packages: 95%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
 Extracting templates from packages: 11%% Extracting templates from packages: 23%% Extracting templates from packages: 35%% Extracting templates from packages: 47%% Extracting templates from packages: 59%% Extracting templates from packages: 71%% Extracting templates from packages: 83%% Extracting templates from packages: 95%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
 Extracting templates from packages: 11%% Extracting templates from packages: 23%% Extracting templates from packages: 35%% Extracting templates from packages: 47%% Extracting templates from packages: 59%% Extracting templates from packages: 71%% Extracting templates from packages: 83%% Extracting templates from packages: 95%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
Setting up tzdata (2011l-0ubuntu0.11.04) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 tzdata 
Setting up tzdata (2011l-0ubuntu0.11.04) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128

---

### Post by raja.genupula on 2011-10-22
Hi man , hope this below link can help you to solve your issue.

[http://ubuntuforums.org/showthread.php?t=1346581](http://ubuntuforums.org/showthread.php?t=1346581)

---

### Post by dwit.udeshi on 2011-11-11
thanks it solved my problem! :)

---

### Post by raja.genupula on 2011-11-11
I am very glad  ...mark your thread as solved from thread tools . 

thank you.

---

