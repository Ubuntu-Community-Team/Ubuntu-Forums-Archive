---
title: "Pre-upgrade question 18.04lts desktop to 20.04lts"
date: 2020-11-20
forum: Installation &amp; Upgrades
---

### Post by Frank P on 2020-11-20
Almost every disto upgrade i've done since 14.04 on a couple of  servers has ended up having to be a clean install because of broken dependencies, etc.  I'd like to avoid that on this desktop if possible. Do I need to do anything about the items shown on the EOL status 
 [COLOR=#000000][FONT=&amp]
ubuntu-support-status --show-unsupported[/FONT][/COLOR]
```

Support status summary of 'xps13':


You have 1759 packages (82.3%) supported until April 2023 (Canonical - 5y)
You have 104 packages (4.9%) supported until April 2021 (Community - 3y)
You have 3 packages (0.1%) supported until April 2021 (Canonical - 3y)


You have 22 packages (1.0%) that can not/no-longer be downloaded
You have 250 packages (11.7%) that are unsupported




No longer downloadable:
beaver-three-eyed-raven-meta canonical-oem-keyring 
dell-0962-bionic-meta dell-0962-meta dell-canonical-estar-logo 
dell-eula dell-recovery dell-recovery-casper dell-super-key 
manage-distro-upgrade manage-estar-settings oem-hotkey-osd 
oem-release oem-seventy-percent-brightness oem-ubuntu-boot-video 
oem-workaround-modprobe-blacklist-hid-sensor-accel-3d sosreport-oem  
timbuktu-meta tlp-config tlp-sensible ubuntu-recovery-grub-hotkey 
workaround-systemd-bluetooth 


Unsupported: 
alacarte apt-transport-https backport-iwlwifi-dkms cinnamon 
cinnamon-common cinnamon-control-center cinnamon-control-center-data 
cinnamon-desktop-data cinnamon-l10n cinnamon-screensaver 
cinnamon-screensaver-x-plugin cinnamon-session 
cinnamon-session-common cinnamon-settings-daemon cjs dconf-editor 
debconf-utils dell-linux-assistant dell-service-meta dia dia-common 
dia-shapes enscript fig2dev geoclue geoclue-ubuntu-geoip 
gir1.2-caribou-1.0 gir1.2-cinnamondesktop-3.0 gir1.2-cmenu-3.0 
gir1.2-cvc-1.0 gir1.2-meta-muffin-0.0 gir1.2-xapp-1.0 gist 
gnome-applets gnome-applets-data gnome-backgrounds gnome-flashback 
gnome-flashback-common gnome-panel gnome-panel-data 
gnome-session-flashback gnome-tweaks google-chrome-stable gpm 
gsfonts-x11 gwakeonlan gyp indicator-applet-complete 
indicator-datetime indicator-printers inkscape insync 
iso-flags-png-320x240 libcaribou-common libcaribou0 
libcinnamon-control-center1 libcinnamon-desktop4 libcinnamon-menu-3-0 
libcjs0 libcscreensaver0 libcvc0 libel-api-java libgeoclue0 libgle3 
libimage-magick-perl libimage-magick-q16-perl libisoburn1 
libjpeg-turbo-progs libjs-async libjs-bowser libjs-events 
libjs-inherits libjs-is-typedarray libjs-jssip libjs-jstimezonedetect 
libjs-merge libjs-node-uuid libjs-rtcninja libjs-sdp-transform 
libjs-typedarray-to-buffer libjs-util libjs-websocket libjsp-api-java 
libmozjs-38-0 libmuffin0 libnemo-extension1 libpanel-applet3 
librhino-java libservlet-api-java libtagsoup-java 
libwebsocket-api-java libwmf-bin libxapp1 mc mc-data meld members 
muffin muffin-common nautilus-compare nemo nemo-data nemo-fileroller 
node-abbrev node-ansi node-ansi-color-table node-archy node-argparse 
node-assert-plus node-async node-balanced-match node-block-stream 
node-bowser node-brace-expansion node-builtin-modules 
node-combined-stream node-concat-map node-config-chain 
node-cookie-jar node-core-js node-core-util-is node-debug 
node-delayed-stream node-es6-promise node-esprima node-events  
node-extsprintf node-forever-agent node-form-data node-fs.realpath 
node-fstream node-fstream-ignore node-github-url-from-git node-glob 
node-graceful-fs node-gyp node-hosted-git-info node-immediate 
node-inflight node-inherits node-ini node-is-builtin-module 
node-is-typedarray node-isexe node-jju node-js-beautify 
node-js-cookie node-js-tokens node-js-yaml node-jsbn node-jschardet 
node-jsesc node-json-buffer node-json-loader node-json-localizer 
node-json-parse-better-errors node-json-parse-helpfulerror 
node-json-schema node-json-schema-traverse node-json-stable-stringify 
node-json-stringify-safe node-json2module node-json3 node-json5 
node-jsonfile node-jsonify node-jsonminify node-jsonparse 
node-jsonselect node-jsonstream node-jsprim node-jssip 
node-jstimezonedetect node-jsv node-jszip node-jszip-utils node-lie 
node-lockfile node-lru-cache node-merge node-mime node-minimatch 
node-mkdirp node-ms node-mute-stream node-nan node-node-uuid 
node-nopt node-normalize-package-data node-npmlog node-once 
node-osenv node-pako node-path-is-absolute node-proto-list 
node-pseudomap node-qs node-read node-read-package-json node-request 
node-retry node-rimraf node-rtcninja node-rw node-sdp-transform 
node-semver node-sha node-slide node-spdx-correct 
node-spdx-expression-parse node-spdx-license-ids node-sprintf-js 
node-tar node-through node-tunnel-agent node-typedarray-to-buffer 
node-underscore node-util node-validate-npm-package-license 
node-verror node-websocket node-which node-wrappy node-yallist 
notify-osd notify-osd-icons npm oem-fix-eth-realtek-disabletlpr8153 
oem-somerville-partner-archive-keyring pepperflashplugin-nonfree  
putty putty-tools python-gi-cairo python-pexpect python-ptyprocess 
python-scour python3-progressbar python3-scour ruby-json scour 
shellcheck somerville-meta syslinux-utils transfig 
ubuntu-touch-sounds xapps-common xorriso xscreensaver-data-extra 
xscreensaver-gl xscreensaver-gl-extra 



```
Thanks
Frank

---

### Post by dino99 on 2020-11-21
As you have some endind packages support in 2021, i suppose you have some non genuine sources or mixed installation.
To avoid dist-upgrade surprise(s), always check you only use genuine sources/packages first; downgrade/uninstall/clean if necessary; then you can upgrade quite surely.

---

### Post by Frank P on 2020-11-21
> **dino99 said:**
> As you have some endind packages support in 2021, i suppose you have some non genuine sources or mixed installation.
To avoid dist-upgrade surprise(s), always check you only use genuine sources/packages first; downgrade/uninstall/clean if necessary; then you can upgrade quite surely.
This is on a new (2 months ago) Dell laptop with 18,04LTS preinstalled.
 I haven't installed any PPAs; All the packages - e.g. Brackets, SublimeText; etc., were done via the Software Updater. I don't recognize most of the entries on the "unsupported" list.I run apt update & apt upgrade nearly every day. 

How can it get into such a mess?

Thanks

Frank

---

