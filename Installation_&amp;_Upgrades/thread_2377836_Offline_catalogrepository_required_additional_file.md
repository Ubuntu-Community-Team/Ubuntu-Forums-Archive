---
title: "Offline catalog/repository required additional files in Ubuntu 16.04"
date: 2017-11-17
forum: Installation &amp; Upgrades
---

### Post by shubhendu.paul on 2017-11-17
Till Ubuntu 14.04, I used to create offline repository for analysis i.e. apt-get and later based on my requirement I will install required packages. In Ubuntu 14.04 I only required Packages.gz file but after migrating to Ubuntu 16.04 the same script is ask for "InRelease" files under SuiteCodename and "Translation-en.gz" under /i18n directories.

[LIST=1]
[*]Could someone help me to understand why these additional files are required?
[*]Is there any way to disable these additional files? If "YES", how?
[/LIST]

Here is my script:-


    ADDTIONAL_OPTION=""
    ANALYSIS_OUT="analysis.out"
    ANALYSIS_ERR="analysis.err"
    CONF_FILE="apt/apt.conf"
    SOURCE_FILE="apt/sources.list"
    
    apt-get check | grep "You might want to run 'apt-get -f install' to correct these"
    if [ "$?" -eq "0" ]
        then
            echo "apt-get check has reported a need to use -f parameter along with -y"
            ADDTIONAL_OPTION="-f"
            echo "Adding -f parameter to apt-get command"
    fi
apt-get --yes -c $CONF_FILE autoclean
apt-get --yes -c $CONF_FILE update >> $ANALYSIS_OUT 2>> $ANALYSIS_ERR
exit_if_err "$?" "apt-get update returned non zero exit code"
# analysis 
apt-get --print-uris --yes -V $ADDTIONAL_OPTION -c $CONF_FILE upgrade >> $ANALYSIS_OUT 2>> $ANALYSIS_ERR
exit_if_err "$?" "apt-get $MODE returned non zero exit code"

---

