---
title: "GUI or CLI Likewise does not join to domain"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by mausilveira on 2009-12-16
Hi all!

I am new to this forum and to Ubuntu and I need some help joining my WS to a windows domain. This is what I got:

Ubuntu fresh new install version 9.10
Likewise installed from the Synaptic Package Manager.
Static IP installed via the Network connection wired GUI.

When I attempted to join to my domain I got the following message:


root@BLDENG005X2MS:/etc/likewise-open5# domainjoin-cli join mydomain.ad.local mydomain\mydomainaccount

Error: Unable to resolve DC name [code 0x00080026]

Resolving 'serverdc02.ani.ad.local' failed. Check that the domain name is correctly entered. Also check that your DNS server is
reachable, and that your system is configured to use DNS in nsswitch. 


I can ping the serverdc02 by name, with no problem. 

Below I have my lsassd.conf and nsswitch.conf files. I have read a lot but could not draw any conclusion on what is wrong, except that a lot of people have absolutely no problem, except me. 
I am getting the same error using the CLI or the GUI from likewise, version 5.0 I believe.

Thank you in advance!

Mau

lsassd.conf file below:

root@BLDENG005X2MS:/etc/likewise-open5# cat lsassd.conf
#
# Likewise Security and Authentication Subsystem (LSASS)
#
# Time value suffixes:
# d - days
# h - hours
# m - minutes
# s - seconds
#

[global]

    # Default: no
    # enable-eventlog = yes    
    
    # Default: yes
    # log-network-connection-events = no

    # Default: \
    # Allowed: a punctuation character
    # Excluded: whitespace, alphanumeric, space-replacement character
    domain-separator = \

[pam]

    # Default: error
    #
    # Note: log-level can be one of
    #       {disabled, error, warning, info, verbose}
    log-level = error
       
    # Message of the day
    # Default: no
    # display-motd = yes
    
    # Note: Show this error when user is not
    #       list of members (users/groups)
    #       allowed to login
    # user-not-allowed-error = Access denied

[auth provider:lsa-activedirectory-provider]

    path = /usr/lib/likewise-open5/liblsass_auth_provider_ad.so

    login-shell-template = /bin/bash
    
    # Prefix path for user's home directory
    # Note:
    #   a) This is used in place of %H in the
    #      homedir-template setting
    #   b) Must be an absolute path
    #
    # Default: Linux: /home
    # Default: MacOS: /Users
    # Default: SunOS: /export/home
    #
    # homedir-prefix = <absolute path>

    homedir-template = %H/%D/%U

    ldap-sign-and-seal = false

    # Cache entry expiration timespan
    # Default: 4h
    # Minimum: 0
    # Maximum: 1d
    cache-entry-expiry = 4h

    # Machine password expiration lifespan
    # Default: 30d
    # Minimum: 1h
    # Maximum: 60d
    machine-password-lifespan = 30d

    # Default: ^
    # Allowed: a punctuation character
    # Excluded: whitespace, alphanumeric, @, /, domain separator character, #
    space-replacement = ^
    
    # Default: no
    # assume-default-domain = yes
    
    # Default: yes
    # sync-system-time = no
    
    # Allow only the following users and groups
    # to login to this system
    #
    # Note: Use a comma-separated list of
    #       { alias, NT4 style name, SID }
    #
    # require-membership-of = ABC\support group, ABC\joe, jane, S-1-5-21-3447809367-3151979076-456401374-513
    
    # Default: yes
    # create-k5login = no

    # Whether home directories should be automatically
    # created upon user login
    #
    # Default: yes
    # create-homedir = no

    # Umask for home directories
    # Default: 022
    #
    # homedir-umask = 022

    # Paths to skeleton directories for provisioning
    # home directories
    #
    # Note: Use a comma separated list
    #
    # Default: /etc/skel
    #   or
    # Default: System/Library/User Template/Non_localized,
    #          /System/Library/User Template/English.lproj
    #
    # skeleton-dirs = /etc/skel

    # Whether user credentials should automatically be
    # refreshed
    #
    # Default: yes
    # refresh-user-credentials = no

    # Forces lsass to use unprovisioned mode
    # Values: full unprovisioned
    # Default: full
    #
    cell-support = unprovisioned

    # Whether to remove a cached group membership entry derived from PAC
    # with information from LDAP showing the user disappearing from
    # a group.
    #
    # Default: yes
    #
    # trim-user-membership = no

    # Whether to return only cached info for NSS group members.
    #
    # Default: yes
    #
    # nss-group-members-query-cache-only = no

    # Whether to return only cached info for NSS user's groups.
    #
    # Default: no
    #
    # nss-user-membership-query-cache-only = yes

[auth provider:lsa-local-provider]

    path = /usr/lib/likewise-open5/liblsass_auth_provider_local.so

    # Default: 30d
    # Minimum: 1d
    # Maximum: 180d
    password-lifespan = 30d

    # Default: 14d
    # Minimum: 1h
    # Maximum: 30d (must be less than lifespan)
    password-change-warning-time = 14d
root@BLDENG005X2MS:/etc/likewise-open5#


nsswitch.conf file:


  root@BLDENG005X2MS:/etc# cat nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
root@BLDENG005X2MS:/etc#

---

### Post by calkrog on 2010-01-12
in your nsswitch.conf file you need to change

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

to

hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4

and i should have no futher problems. hope it helps :)

---

