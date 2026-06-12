---
title: "Request Tracker email out. Postfix or SSMTP not working."
date: 2013-05-26
forum: Installation &amp; Upgrades
---

### Post by RoosterHam on 2013-05-26
So I'm trying to configure Request Tracker 4. RT doesn't need to recieve emails, as yet, but I'd like to configure it to send emails to collegues tho whom I assign tickets.

Our email is handled outside of our company. I have tried to configure RT to use Postfix to send emails through our 'smarthost' but but /var/log/mail.log tells me "unkown user:"

OS is Ubuntu 12.10.

the following is how I set up postfix:
dpkg-reconfigure postfix
tar cfz /var/backups/etc-postfix_20130526.tgz /etc/postfix/
echo "mail.mycompany.com [email]rtfour@mycompany.com[/email]:RT4Password" >>/etc/postfix/sasl_passwd
chmod 600 /etc/postfix/sasl_passwd
chown root:root /etc/postfix/sasl_passwd
postmap /etc/postfix/sasl_passwd
postconf -e "relayhost = [mail.mycompany]:587"
postconf -e "smtp_sasl_auth_enable = yes"
postconf -e "smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd"
postconf -e "smtp_sasl_security_options = "
postconf -e "smtp_use_tls = yes"
postfix check
postfix reload

that sends no email and tells me "unkown user:"

None of the online help seems to add anything for basic configuration. So I thought perhaps I could use ssmtp as I did with my nagios host. Unfotunately, while nagios was easy to get sending via ssmtp. RT still doesn't work. ssmtp is woking now. I can send mail from the cli.

What would I need to do to get RT to send email via ssmtp? Or what do I need to fix to get postfix to work?

---

