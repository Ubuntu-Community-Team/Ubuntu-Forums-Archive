---
title: "Sendmail: No AUTH available / No secret found in database"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by pittcaleb on 2006-04-28
We are experiencing multiple issues with Sendmail authentication and
have combed the Internet for a solution to no avail and any help would
be appreciated.

We are using Linux, Ubuntu distribution (latest CD release).  The
situation is we are reselling email access and need to be able to allow
uses to come in, authenticate via the passwd file, and send out / relay
mail.  We are using Sendmail 8.13.4/8.13.4 and Cyrus-SASL 2.1.19.

The first problem we ran into is that whenever we attempted to
authenticate, we'd get

Apr 21 10:50:37 localhost sm-mta[5595]: no secret in database

and it would fail.

In the midst of testing this out, I found that if I added
authentication configuration information to the .mc file, in particular

TRUST_AUTH_MECH(`LOGIN PLAIN')
define(`confAUTH_MECHANISMS',`LOGIN PLAIN')
define(`confAUTH_OPTIONS',`y,p,a')

all of a sudden the AUTH command would disappear!

Somehow, I managed to add something else to the configuration, either
the saslauthd configuration or something else, and it did the same
thing, except I can't figure out what it was that caused it to
disappear.

We've read [http://www.sendmail.org/~ca/email/auth.html](http://www.sendmail.org/~ca/email/auth.html),
[http://www.sendmail.org/~ca/email/authrealms.html](http://www.sendmail.org/~ca/email/authrealms.html), the Sendmail FAQs,
the Sendmail section on relaying and virtual domains, and many relevant
Google hits and posts from c.m.s.

We enabled debugging and the only thing we get out of that is

Apr 26 11:51:51 localhost sm-mta[29525]: AUTH warning: no mechanisms

Oh, I configured the SASL library with

LOCAL_CONFIG
ESASL_PATH=/usr/lib/sasl2

at the end of my sendmail.mc file, and it appears in the sendmail.cf
which seems good.

There seems to be some issue with SASL libraries we can't figure out
for certain.  They are supposed to be linked in particular way per
auth.html.  Someone suggested that you needed to link the .so file to
the .so.x file rather than the .so.x.y.z file; I can't see how this
makes a difference from a filesystem perspective but I tried it anyway
(on libplain), to no avail.  I ran the crtln.sh script in there which
made no change.  Here is an example of the libraries' listing:

-rwxrwxr-x  1 root root 13502 2005-09-05 09:45 libplain.a
-rwxrwxr-x  1 root root   831 2005-09-05 09:45 libplain.la
lrwxrwxrwx  1 root root    13 2006-04-26 11:16 libplain.so ->
libplain.so.2
lrwxrwxrwx  1 root root    18 2006-04-01 06:06 libplain.so.2 ->
libplain.so.2.0.19
-rwxrwxr-x  1 root root 13240 2005-09-05 09:45 libplain.so.2.0.19
-rw-rw-r--  1 root root 21038 2005-09-05 09:45 libsasldb.a
-rw-rw-r--  1 root root   852 2005-09-05 09:45 libsasldb.la
lrwxrwxrwx  1 root root    19 2006-04-01 06:06 libsasldb.so ->
libsasldb.so.2.0.19
lrwxrwxrwx  1 root root    19 2006-04-01 06:06 libsasldb.so.2 ->
libsasldb.so.2.0.19
-rw-rw-r--  1 root root 17352 2005-09-05 09:45 libsasldb.so.2.0.19

auth.html says:
"If you have installed a library or another SASL related file and
sendmail doesn't seem to use it, do the following: make the file group
writable and start (-Am is only required for 8.12 (and later), if you
run an older version omit it)

sendmail -O LogLevel=14 -bs -Am
EHLO localhost
QUIT

and then check the logfile: it must have an error now for that file. If
it doesn't, then your configuration is wrong (check your parameters for
configure (SASL) and all the paths)."

I did that, I see nothing in the log file.  I have been playing around
with Sendmail.conf and /etc/default/saslauthd and they seem correct.  I
am not sure what is meant by "all the paths"; I fixed that one path but
I'm not sure what other paths to look at.

/usr/lib/sendmail -d0.1 -bv root returns:

 Compiled with: DNSMAP LDAPMAP LOG MAP_REGEX MATCHGECOS MILTER MIME7TO8
                MIME8TO7 NAMED_BIND NETINET NETINET6 NETUNIX NEWDB NIS
NISPLUS
                PIPELINING SASLv2 SCANF SOCKETMAP STARTTLS USERDB
USE_LDAP_INIT
                XDEBUG

Here are various config files.  You can see configurations I've been
playing around with in the comments.

#########################################################
# sendmail. mc ############################################
#########################################################
# headers and some comments omitted
divert(0)dnl
define(`_USE_ETC_MAIL_')dnl
include(`/usr/share/sendmail/cf/m4/cf.m4')dnl
VERSIONID(`$Id: sendmail.mc, v 8.13.4-3 2005-06-04 09:31:03 cowboy Exp
$')
OSTYPE(`debian')dnl
DOMAIN(`debian-mta')dnl
dnl # Items controlled by /etc/mail/sendmail.conf - DO NOT TOUCH HERE
undefine(`confHOST_STATUS_DIRECTORY')dnl        #DAEMON_HOSTSTATS=
undefine(`UUCP_RELAY')
undefine(`BITNET_RELAY')
dnl #
dnl # General defines
dnl #
FEATURE(`no_default_msa')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MTA-v6, Port=smtp, Addr=::1')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MSP-v6, Port=submission,
Addr=::1')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission')dnl
dnl #
dnl # Be somewhat anal in what we allow
#define( sm_enable_auth,`yes')
#define(`confAUTH_OPTIONS', `A')dnl

#TRUST_AUTH_MECH(`LOGIN DIGEST-MD5 PLAIN')
TRUST_AUTH_MECH(`LOGIN PLAIN')
#define(`confAUTH_MECHANISMS',`LOGIN PLAIN DIGEST-MD5')
define(`confAUTH_MECHANISMS',`LOGIN PLAIN')
define(`confAUTH_OPTIONS',`y,p,a')
define(`confLOG_LEVEL',`14')dnl
define(`confPRIVACY_FLAGS',dnl
`needmailhelo,needexpnhelo,needvrfyhelo,restrictqrun,restrictexpand,nobodyreturn,authwarnings')dnl
define(`confCONNECTION_RATE_THROTTLE', `15')dnl
define(`confCONNECTION_RATE_WINDOW_SIZE',`10m')dnl
dnl #
dnl # Features
dnl #
dnl # The access db is the basis for most of sendmail's checking
FEATURE(`access_db', , `skip')dnl
FEATURE(`greet_pause', `1000')dnl 1 seconds
FEATURE(`delay_checks', `friend', `n')dnl
define(`confBAD_RCPT_THROTTLE',`3')dnl
FEATURE(`conncontrol', `nodelay', `terminate')dnl
FEATURE(`ratecontrol', `nodelay', `terminate')dnl
FEATURE(`always_add_domain')dnl
#FEATURE(`allmasquerade')dnl

dnl # Masquerading options
MASQUERADE_AS(`mockingbird-productions.com')dnl
#FEATURE(`masquerade_envelope')dnl
FEATURE(use_cw_file)
FEATURE(limited_masquerade)
FEATURE(local_no_masquerade)
FEATURE(`genericstable')
FEATURE(`virtusertable')
FEATURE(`nocanonify')
MAILER_DEFINITIONS
MAILER(`local')dnl
MAILER(`smtp')dnl
LOCAL_CONFIG
ESASL_PATH=/usr/lib/sasl2

#########################################################
# /etc/default/saslauthd #####################################
#########################################################

# This needs to be uncommented before saslauthd will be run
automatically
START=yes

#PARAMS="-m /var/spool/postfix/var/run/saslauthd"
PARAMS="-m /var/run/sendmail/mta/"

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
MECHANISMS="shadow"
#MECHANISMS="pam shadow"

#MECHANISMS="pam"

#########################################################
# Sendmail.conf ###########################################
#########################################################

#Currently configurable parameters:
#- srvtab (for KERBEROS_V4): [/etc/srvtab] path
#        where to find the srvtab
#
#- pwcheck_method: [PAM] one of {PAM, kerberos_v4, passwd, shadow,
sasldb}
#        how to check plaintext passwords.
#
#- auto_transition: [false]
#        if true, automatically add secrets to the secret database when
#        PLAIN or check_password is used, so in the future the user can
#        use the more secure mechanisms.
#
#*** For a more detailed guide on configuring SASL, please look at
#doc/sysadmin.html.
#
auto_transition: true
pwcheck_method: passwd
#pwcheck_method: shadow
#pwcheck_method: saslauthd
#pwcheck_method: sasldb
#pwcheck_method: auxprop saslauthd
auxprop_plugin: sasldb
allowanonymouslogin: 0
allowplaintext: 1
#mech_list: EXTERNAL DIGEST-MD5 CRAM-MD5 LOGIN PLAIN
mech_list: EXTERNAL LOGIN PLAIN

#########################################################
# saslauth.conf ############################################
#########################################################
#auto_transition: true
pwcheck_method: saslauthd
#auxprop_plugin: sasldb
allowanonymouslogin: 0
allowplaintext: 1
mech_list: PLAIN LOGIN CRAM-MD5 DIGEST-MD5

############################################

I hope that's enough information.  We've done our best to do our due
diligence until we reach our wit's end.  Any help would be gratefully
appreciated.

---

