# Tips for improving experience on mainstream GNU/Linux

This project targets at making Ubuntu/Fedora easy to use. Improvements will keep adding to the repo, wish you enjoy it.

Don't hesitate to suggest if you have any good ideas.

# Tested Models

- Dell Precision M3800/XPS 15 9530
- Dell XPS 13 9350/9360
- [HP Elite c1030 (Chromebook with coreboot)](https://github.com/syscl/LinuxLand/blob/master/Fedora.md)
- [Asus Chromebox 3 (with coreboot)](https://github.com/syscl/LinuxLand/blob/master/Fedora.md)
- Asus x205ta
- Asus VivoBook E12 E203NAS
- Raspberry Pi 3 (rev. B) & Raspberry Pi 4
- Lenovo ThinkStation P520
- [Kindle Paperwhite 3-5, Scribe](https://github.com/syscl/LinuxLand/blob/master/Kindle.md)

# Softwares & Optimizations

- [VSCode](https://code.visualstudio.com) for code editing.
- To download youtube video with best video quality (e.g. 1080p) + best audio, use [yt-dlp](https://github.com/yt-dlp/yt-dlp) for a given video: `yt-dlp -f "bv+ba/b" <video-link>`
- [Eternal Terminal](https://eternalterminal.dev/) `et -c 'tmux -CC' pi@<addr>`
- [Sublime text](https://www.sublimetext.com/)
- [Firefox](https://www.mozilla.org/en-US/firefox/)
- [gnome-sushi](https://gitlab.gnome.org/GNOME/sushi): a quick previewer for Nautilus use space bar
- [gnome-weather](https://apps.gnome.org/en/Weather/): `sudo apt install gnome-weather`
- [Cherrytree](http://www.giuspen.com/cherrytree/)
- [Netease music](http://music.163.com/)
- [GoldenDict](https://github.com/goldendict/goldendict)
- [Youdao dict](http://cidian.youdao.com/)
- [Clang](http://llvm.org/)
- [Sogou Pinyin](http://pinyin.sogou.com/linux/?r=pinyin)
- [IntelliJ IDEA](https://www.jetbrains.com/idea/)
- [Typora](http://www.typora.io/#)
- [WPS](https://www.wps.com/linux)
- [DiffMerge](https://sourcegear.com/diffmerge/)
- [Pinta](https://pinta-project.com/pintaproject/pinta/)
- [vlmcsd](https://github.com/Wind4/vlmcsd)
- [Lantern](https://github.com/getlantern/lantern)
- [Gummi](https://github.com/alexandervdm/gummi/wiki/Installing-Gummi)
- Encryption [KeePassXC](https://keepassxc.org/) for Linux, macOS and Windows
  - Use **KeePassDX** for Android
  - Use **KeePassium** for iOS
- [Simplenotes](https://simplenote.com/)
- [netdata](https://my-netdata.io)
- [Excalidraw](https://github.com/excalidraw/excalidraw) drawing diagram
- [hyper](https://hyper.is/plugins/hyper-native)
- Apache
- [FileZilla](https://filezilla-project.org)
- [btop](https://github.com/aristocratos/btop) a htop/top alternative
- git
```
sudo apt-get install git
```
- deepin scrot/screenshot
```sh
sudo apt-get install python-xlib
```
- Change tty font style
Though Ubuntu gave me a beautiful UI, I still want my console font classic and clean, that's why I choose VGA font in this case. Change step will be the following:
```sh
sudo dpkg-reconfigure console-setup
```
```Font for the console```->```VGA``` or ```Do not change the boot/kernel font```

- extfat support
```sh
sudo apt install exfat-fuse exfat-utils
```
- Resolve VI/VIM arrow keys binding issue
```sh
sudo apt install vim
```

- Sogou fcitx install steps
```sh
sudo apt install fcitx
sudo dpkg -i [package-of-sogou].deb
sudo apt-get install -f
```

# Fonts for Linux
Fonts is important and worth a section for discussing it. I used `Gnome Tweaks` to change system fonts, here are the settings:
- `Interface Text` and `Document Text`: `Helvetica Regular 10`
- `Legacy Window Titles`: `Helvetica Bold 11`
- `Monospace Text`: `SF Mono Regular 10`
- [DM Mono](https://fonts.google.com/specimen/DM+Mono) is great for website code block

## Firefox Fonts
LatIn (refers macOS):

- `Proportional`: `Serif`, `Size`: `16`
- `Serif`: `Times`
- `Sans-serif`: `Helvetica`
- `Monospace`: `Menlo`, `Size`: `13`

Chinese(refers to macOS):

- `Proportional`: `Sans Serif`, `Size`: `16`
- `Serif`: `Times New Roman`
- `Sans-serif`: `Arial`
- `Monospace`: `Menlo`, `Size`: `16`

## Chromium fonts

- `Sans-serif font`: `Helvetica`
- `Mathematical font`: `STIX Two Math` [link](https://github.com/stipub/stixfonts)

- Change system fonts
```gconftool-2``` has been superseeded by ```gsettings``` on Ubuntu ```16.04+``` and in other GNOME based systems.

Nowadays you can simply run the following in a terminal to change/reset all your desktop font settings:

```sh
# change windows title
gsettings set org.gnome.desktop.wm.preferences titlebar-font 'Microsoft YaHei UI 11'
gsettings set org.gnome.desktop.interface document-font-name 'Microsoft YaHei UI 11'
# default font
gsettings set org.gnome.desktop.interface font-name 'Microsoft YaHei 11 UI'
# monospace-font
gsettings set org.gnome.desktop.interface monospace-font-name 'SF Mono Extra-Condensed 12'
gsettings set org.gnome.nautilus.desktop font '' # default font '', leave blank
```

`SF Mono` is more preferrable from macOS: `/System/Applications/Utilities/Terminal.app/Contents/Resources/Fonts`
In macOS: open Fonts within `/System/Applications/Utilities/Terminal.app/Contents/Resources/Fonts` then install it. `SF Mono - Medium`  is my new favour.

To reset above setting, just simply type in
```sh
gsettings reset org.gnome.desktop.interface font-name
gsettings reset org.gnome.desktop.interface document-font-name
gsettings reset org.gnome.desktop.interface monospace-font-name
gsettings reset org.gnome.desktop.wm.preferences titlebar-font
gsettings reset org.gnome.nautilus.desktop font
gsettings reset org.gnome.desktop.interface text-scaling-factor
```

# tmux

It is highly recommend to use tmux for both your dev server or local machine because of its multiplex feature.

```sh
sudo apt install tmux
```

Make the tmux launch for every terminal, append the following lines at the end of the ```.bashrc```

```sh
if command -v tmux &> /dev/null && [ -n "$PS1" ] && [[ ! "$TERM" =~ screen ]] && [[ ! "$TERM" =~ tmux ]] && [ -z "$TMUX" ]; then
  exec tmux
fi
```

The above command is going to make sure that

```
 (1) tmux exists on the system
 (2) we're in an interactive shell
 (3) tmux doesn't try to run within itself
```

# Tmux connection command I use at work
alias devvm="ssh ${cloudtop_address} -oCompression=yes -oCheckHostIP=no -oServerAliveInterval=60 -t -- '\''tmx2 -CC new -A -s work'\'"

Reference:

- [Using bash's command to check for existence of a command](http://man7.org/linux/man-pages/man1/bash.1.html#SHELL_BUILTIN_COMMANDS)
- [Why to use command instead of which to check for the existence of commands](https://unix.stackexchange.com/a/85250)
- [Using $PS1 to check for interactive shell](https://www.gnu.org/software/bash/manual/html_node/Is-this-Shell-Interactive_003f.html)
- [Expected state of $TERM environment variable "for all programs running inside tmux"](http://man7.org/linux/man-pages/man1/tmux.1.html#WINDOWS_AND_PANES)
- [Start tmux on every shell login](<https://wiki.archlinux.org/index.php/Tmux#Start_tmux_on_every_shell_login>)

Enable mouse scroll:

- echo 'set -g mouse on' >> ~/.tmux.conf
- To select or copy in tmux, press ```Fn``` key in Linux (macOS use ```Option```)
- More settings can be referred to: <https://github.com/gpakosz/.tmux>

## Enable mouse selection and copy/paste for tmux
One may notice that copy is not as natural as default terminal - i.e. mouse select + copy shortcut. To fix this, you need to add install tpm and `tmux-yank`:
1. Install tmux plugin manager (tpm): https://github.com/tmux-plugins/tpm
2. Add `set -g @plugin 'tmux-plugins/tmux-yank'` to ~/.tmux.conf
3. In tmux, invoke `<prefix-key>+I` to trigger the `tmux-yank` install

You can select-to-copy effienctly.

## Add cpu and memory utilization for tmux
1. Install tmux plugin manager (tpm): https://github.com/tmux-plugins/tpm
2. Install tmux cpu and gpu stats: https://github.com/tmux-plugins/tmux-cpu
3. Set the following config in tmux.conf
```
# cpu stats
set -g @plugin 'tmux-plugins/tmux-cpu'
# in .tmux.conf
set -g status-right '#{cpu_bg_color} CPU:#{cpu_percentage} MEM:#{ram_percentage}'
```

# Albert (similar to Alfred and Spotlight in macOS)

This ultimately improve your productivity. Check here for [installation](https://albertlauncher.github.io/docs/installing/)

- To enable quick search: settings (on the top right of the box) - Extensions - WebSearch - Trigger. For example change ``gg`` to `g` for Google

# Fuzzy auto completion in terminal

For an enhancement of `Ctrl+R` refer [here](https://github.com/junegunn/fzf)

> An alternative shell magic history using [Atuin](https://atuin.sh/). `enter_accept` is set to true by default, which means default enter to the selection will execute the command. To change the selected item, just hit `tab` instead of `enter`. Documents about more settings [here](https://docs.atuin.sh/configuration/config).

For ```Ubuntu``` specific:

```sh
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

# Ubuntu the following packages have been kept back
Please refer to [this](https://askubuntu.com/questions/601/the-following-packages-have-been-kept-back-why-and-how-do-i-solve-it):
Solution 1:
```
sudo apt-get --with-new-pkgs upgrade <list of packages kept back>
```
Solution 2:
```
sudo apt-get install <list of packages kept back>
```

# Edit binary

- Vi/Vim: ```:%!xxd``` to enter hex edit mode, ```:!xxd -r``` to quit
- Or use command line hex edit by ```apt install hexedit```

# Dynamic Wallpaper

```Gnome``` actually supports the dynamic wallpaper around 10 years ago, and recently macOS Majove has bought this function to macOS. To enable this beautiful function that is built-in Gnome, we have to load a customize ```xml``` as desktop and lock screen background as following:

```sh
mkdir -p ~/Pictures/Wallpapers/majove_dynamic
curl -o ~/Pictures/Wallpapers/majove_dynamic/majove.xml https://github.com/syscl/Ubuntu4Laptops/blob/master/dynamic_wallpapers/majove.xml
```

Open the ```~/Pictures/Wallpapers/majove_dynamic/majove.xml ```, change the ```username``` from ```syscl``` to the user name you used, then unzip all the wallpapers from [here](https://files.rb.gd/mojave_dynamic.zip) to ```~/Pictures/Wallpapaers/majove_dynamic```

Set up the lock screen and desktop background by the following

```sh
gsettings set org.gnome.desktop.background picture-uri 'file:///home/syscl/Pictures/Wallpapers/mojave_dynamic/mojave.xml'
gsettings set org.gnome.desktop.screensaver picture-uri 'file:///home/syscl/Pictures/Wallpapers/mojave_dynamic/mojave.xml'
```

```Note``` Change the ```syscl``` to the user name you used on the above command line.



# Remove/hide icons in the ```Show Applications``` button

Jump right into the ```/usr/share/applications``` directory in the terminal, and remove/hide the icons you want. For example, remove the deprecated ```reboot```, ```shut down``` and ```logout``` button when updating from Unity to Gnome

```sh
cd /usr/share/applications
sudo rm -rf reboot.desktop shutdown.desktop logout.desktop
```

# vlmcsd

Install compiled binaries to ```/usr/local/bin/vlmcsd```, then execute ```vlmcsd``` then ```vlmcs``` to start the server. Then on ```Windows``` client, open ```cmd``` as Administration, run the following:
```sh
slmgr -ipk <GLVKs Key>
slmgr -skms <vlmcsd server address>
slmgr -ato
slmgr -dlv
```

# Install GoldenDict

- Installing External Deps on Ubuntu
```sh
sudo apt-get install git pkg-config build-essential qt4-qmake \
     libvorbis-dev zlib1g-dev libhunspell-dev x11proto-record-dev \
     libqt4-dev libqtwebkit-dev libxtst-dev liblzo2-dev libbz2-dev \
     libao-dev libavutil-dev libavformat-dev libtiff5-dev libeb16-dev
```
- Download the latest GoldenDict
```sh
git clone git://github.com/goldendict/goldendict.git
```
- Build it by the following
```sh
cd goldendict && qmake-qt4 && make
```

Note: to compile with ```libhunspell``` older than 1.5, use the following command to build instead

```sh
cd goldendict && qmake-qt4 "CONFIG+=old_hunspell" && make
```

- Install the binary to ```/usr/share/local``` by
```sh
make install
# sudo mv /usr/local/share/applications/goldendict.desktop ~/.local/share/applications # correct the *.desktop path
```
System tray disappear on Ubuntu 18.04 (Gnome)

Install ```sni-qt``` libraries: ```apt install sni-qt```

# Tune GoldenDict

- Install translate-shell by ```apt install translate-shell```

- Add the following to ```Edit```->```Dictionaries```->```Sources```->```Programs```:
  1. Enabled, Typed=```Plain Text```, Name: [EN->ZH], Command Line: ```trans -e google -s en -t zh -show-original y -show-original-phonetics n -show-translation y -no-ansi -show-translation-phonetics n -show-prompt-message n -show-languages y -show-original-dictionary n -show-dictionary n -show-alternatives n "%GDWORD%"```
  2. Enabled, Typed=```Plain Text```, Name: [ZH->EN], Command Line: ```trans -e google -s fr -t en -show-original y -show-original-phonetics n -show-translation y -no-ansi -show-translation-phonetics n -show-prompt-message n -show-languages y -show-original-dictionary n -show-dictionary n -show-alternatives n "%GDWORD%"```

  - For extra dictionaries you can refer to ```software/GoldenDict/dictionary``` folder under this git repo
  - Changing the font and size for GoldenDict, use the following:

  ```sh
  echo 'body'  							  >~/.goldendict/article-style.css
  echo '{'    							 >>~/.goldendict/article-style.css\
  echo '    font-family: Microsoft YaHei;' >>~/.goldendict/article-style.css\
  echo '    font-size: 12px;'              >>~/.goldendict/article-style.css\
  echo '}'                                 >>~/.goldendict/article-style.css\
  ```

  More setting details please refer [here](http://goldendict.org/wiki/index.php/FAQ).

# svn

```sh
sudo apt install subversion
```

# Install Ubuntu/Debian on F2FS
This is a note for temporarily install Debian or Debian-like Distros on F2FS, tested on P520, E203 and raspberry pi (EFI + root partition). The basic idea is copying and updating initramfs:
- Install system as root on EXT4/EXT2
- Install `f2fs-tools` to the current system
- Add the following to the `/etc/initramfs-tools/modules`:
```
f2fs
fscrypto
crc32-pclmul
crc32c_generic
crc32c-intel
crc32_generic
libcrc32c
```
- Create F2FS partition by command `mkfs.f2fs /dev/sd<diskNum><partNum> -f`
- Mount F2FS partition to /mnt
- Sync the current partition content to a temp disk: `sudo rsync -HPXax / /mnt`
- Once sync has completed, prepare for chroot:
```sh
for type in dev sys proc run boot boot/efi sudo mount --bind /dev /mnt/$type
```
- Noted down the f2fs partition's UUID `sudo blkid|grep f2fs`
- Change the root in `/mnt/etc/fstab` to the new UUID
- Change `ext4` to `f2fs` and `errors=remount-ro` to `noatime`.
- Access the chroot environment to update its initramfs and get it set up in grub:
```sh
sudo chroot /mnt
update-initramfs
update-grub2
exit
```
- Cleanly unmount the target system's mounts
```
sudo unmount /mnt/boot/efi
sudo unmount /mnt/*
sudo unmount /mnt
```
- Reboot the system

Note:
- For one disk installation, you can created three partitions: 1) EFI 2) Large F2FS chunck 3) 10G EXT4 as initial root. Once you completed the installation, move EXT4 to F2FS and resize the partition (I haven't got `resize.f2fs` succeed yet)
- It's better to have two disks to finish the copy and swap procedure, this way you can fully maximize the F2FS on the disk


# Optimize ```libreoffice```

- Close the startup logo in /etc/libreoffice/sofficerc : ```Logo=1``` --> ```Logo=0```

- Notice in ```Libreoffice``` 5.3.x, there's no more ```sofficerc``` in ```/etc/libreoffice``` thus we need to search where the ```Logo=``` argument located in, here's the procedure

  ```sh
  grep -l -r -i 'Logo=' /opt/libreoffice*
  ```

This will give you the correct path of the configuration location, change ```Logo=1``` to ```Logo=0```

# ```HiDPI``` for Netease Music Player (temporary)
Since Netease Music under Linux is achieved through Qt5, most elements are drawn by WebKit by a forking of Chromium, so we can just simply pass an startup argument ```--force-device-scale-factor=2``` for ```netease-cloud-music```, simply touch the ```/usr/share/applications/netease-cloud-music.desktop```, change ```Exec=netease-cloud-music %U``` to ```Exec=netease-cloud-music --force-device-scale-factor=2 %U```

# Optimize ```foxitreader```
- Install program by
```sh
sudo ./FoxitReader.run
```
- Set installation folder as ```/opt/foxitreader``` instead of ```~/opt/foxitreader```

- Fixe files' permission
```sh
sudo chown -R $USER:$USER /opt/foxitreader
```
- Correct the ```~/.local/share/applications/FoxitReader.desktop```  ```Icon=<*>``` to ```/usr/share/icons/hicolor/64x64/apps/FoxitReader.png```
- Optimize/remove FoxitReader ```cloud plugin``` (previous cause the system draining 100% of CPU resources)
```sh
sudo rm -r /opt/foxitreader/fxplugins
```

# Install ```pinying```
## On Ubuntu 24.04
1. It is recommended to install fcitx5 and cloudpinyin for pinyin input. A brief description of installing pinyin addon
```
sudo apt install fcitx5 fcitx5-chinese-addons fcitx5-frontend-gtk3
```
2. Open Settings -> Keyboard -> Input Source, remove Chinese Pinyin from the list.
3. Run `im-config`, follow the wizard and choose fcitx5 as IME.

4. Run `sudo vi /etc/environment` and add below environment variables:
```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```
This step is important, without it you will be unable to switch IME in most of the applications.

5. Open Tweaks (install by sudo apt install gnome-tweaks) and add Fcitx 5 to Startup Applications.

6. Reboot


## On Ubuntu 16.04-22.04
- On Ubuntu 18.04-22.04, to install sogou pinyin please refer to [guide](https://shurufa.sogou.com/linux/guide) and :
```
sudo apt purge ibus

sudo apt install libqt5qml5 libqt5quick5 libqt5quickwidgets5 qml-module-qtquick2

sudo apt install libgsettings-qt1

sudo cp /usr/share/applications/fcitx.desktop /etc/xdg/autostart/

sudo dpkg -i <sogou-pinyin>.deb; sudo apt install -f
```

# Install ```Aria2``` and ```Aria2 WebUI``` for off line download on Raspberry Pi

```sh
apt install aria2
mkdir ~/.aria2
```

Attach the below contents to ```~/.aria2/aria.conf```

```
dir=/home/pi/downloads
file-allocation=falloc
continue
log-level=error
max-connection-per-server=4
summary-interval=120
daemon=true
enable-rpc=true
rpc-listen-port=6800
rpc-listen-all=true
max-concurrent-downloads=1
disable-ipv6=true
disk-cache=25M
timeout=600
retry-wait=30
max-tries=50
```

This is a sample of the configuration, you can tune it as you like. Now create the launch init.d scirpt by the following script under ```/etc/init.d/aria2

```sh
#!/bin/sh
# /etc/init.d/aria2

### BEGIN INIT INFO
# Provides: aria2cRPC
# Required-Start: $network $local_fs $remote_fs
# Required-Stop: $network $local_fs $remote_fs
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: aria2c RPC init script.
# Description: Starts and stops aria2 RPC services.
### END INIT INFO

RETVAL=0
case “$1” in
start)
echo -n “Starting aria2c daemon ”
umask 0000
aria2c –daemon=true –enable-rpc –rpc-listen-all -D –conf-path=/home/pi/.aria2/aria2.conf
RETVAL=$?
echo
;;
stop)
echo -n “Shutting down aria2c daemon ”
/usr/bin/killall aria2c
RETVAL=$?
echo
;;
restart)
stop
sleep 3
start
;;
*)
echo $”Usage: $0 {start|stop|restart}”
RETVAL=1
esac
exit $RETVAL
```

Attach executable permission for the script just touched (chmod +x aria) then update rc script

```shell
sudo update-rc.d aria2 defaults
```

Now we turn to install the ```Aria2 WebUI```

- Download the latest version of ```Aria2 WebUI``` from [here](https://github.com/ziahamza/webui-aria2), we actually want the build files under ```docs```, copy the ```docs``` directory to ```/var/www/html``` as aria2 (so that we can access it directly).

# Samba on Raspberry Pi

Please refer to this [link](https://tutorials.ubuntu.com/tutorial/install-and-configure-samba#3) first, full document will be appended later on.

# Remove unused ibus

Since I use sogou pinyin with ifcitx as my major input source, so that ibus is not required on my system, remove it by ```apt purge ibus indicator-keyboard```

# Dash to Dock configuration

- Ubuntu dash to dock (modified version of dash to dock):

Reset ```transparent-mode``` to ```'ADAPTIVE'```:

```sh
gsettings reset org.gnome.shell.extensions.dash-to-dock transparency-mode
```

Reset ```min-alpha``` to default

```sh
gsettings reset org.gnome.shell.extensions.dash-to-dock min-alpha
```

- Original dash to dock extension:

Recommend style set to ```Dots```, and the rest are the same as Ubuntu dash-to-dock.

But if this is not enough to reset all settings, try to remove and reinstall the whole directories under ```/usr/share/gnome-shell/extensions```

# Sublime text as default editor

- Please refer [here](http://superuser.com/questions/704046/change-default-text-editor-to-sublime-text-in-linux-mint)

# Install FileZilla

- Open terminal(Crtl+Alt+T)

```shell
sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu xenial-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'
```

- Install the GPG key so that apt package manager will trust the packages from that repository via command

```shell
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

- Now it's time to install

```shell
sudo apt update && sudo apt install filezilla
```



# Use ```black``` cursor instead of ```white``` cursor

The problem of using Unity Tweak Tool(a very powerful tool) is that Unity Tweak Tool can not change the cursor entirely. In login mode, we still can see the origin system default cursor. And sometimes, the black cursor will be reversed due to some system bug. Thus the permanent solution will be replace the whole white mouse cursor to a black one, here's the solution

```sh
mv -r /usr/share/icons/DMZ-White /usr/share/icons/DMZ-White-bak
cp -r /usr/share/icons/DMZ-Black /usr/share/icons/DMZ-White
```

Reboot, now you can enjoy a nice black mouse cursor.

For those who enjoy macOS cursor, here's a high quality macOS cursor under icons/cursor/macOS, you just place ```macOS/cursor``` under ```/usr/share/icons/DMZ-White``` . Reboot to enjoy the nice macOS(Sierra icons).



# Customize application's icon and name

The icon and the name of the application is sometimes not as our expected, in other words, the icon is pretty ugly and the name is not straightforward... So to change the icon, the first step you need to do is copy the icon files to ```~/.local/share/icons/hicolor/<icon_pixelxicon_pixel>/apps```(```arugments``` decided by the icon pixel), then change the <application>.desktop file under ```/usr/share/applications```. For example, I want to change the ```Simplenotes``` icon and name to ```notes.png``` and ```Notes``` respectively, open simplenote.desktop and change the value to ```Icon=Icon=/home/<username>/.local/share/icons/hicolor/128x128/apps/notes.png``` and ```Name=Notes``` respectively.

# ```Drag lock``` and ```Palm rejection```

Once I've switched to ```Ubuntu```, I soon realized the function of the trackpad loses drag lock and palm rejection which make the trackpad almost unable to use.  Thus I do some research about how to tune with it, here's the [solution](https://github.com/syscl/Ubuntu4Laptops/commit/d739b107be787bc05413aa5237d9705971b65c67).

After applying the patch, you will soon enjoy the trackpad on Ubuntu.

- For ```3``` finger gestures for example: back a page:

```sh
synclient "TapButton3" "8"
```

## [Caffein Gnome Extension](https://github.com/eonpatapon/gnome-shell-extension-caffeine)
Install it, configured it to show in the status bar. Enable/disable it by scroll mouse on the icon.



# Install LaTex

Before you install the latest LaTex, you should remove older version to avoid conflict just in case

```sh
sudo dpkg --purge --force-all texlive-xetex
sudo dpkg --purge --force-all texlive-math-extra
```

Then install LaTex now

```sh
sudo add-apt-repository ppa:jonathonf/texlive
sudo apt-get install texlive
sudo apt-get install texlive-fonts-recommended texlive-fonts-extra
```

Fix the [loss of section numbering with the new update](https://tex.stackexchange.com/questions/299969/titlesec-loss-of-section-numbering-with-the-new-update-2016-03-15) issue

```sh
sudo wget http://mirrors.ctan.org/macros/latex/contrib/titlesec/titlesec.sty -O /usr/share/texlive/texmf-dist/tex/latex/titlesec/titlesec.sty
```



# Install JDK

```sh
apt-get install default-jdk
```

# No such native application org.gnome.chrome_gnome_shell
This is because the missing [gnome-browser-connector](https://wiki.gnome.org/Projects/GnomeShellIntegration/Installation). Install it to fix installing gnome extension issues.

> Note: Bing Wallpaper is a nice extension for gnome

# Enable swipe back and forward for chrome on Wayland
This is a tricky feature that Firefox support while chromium base browser missing. Enable it by adding this `--enable-features=TouchpadOverscrollHistoryNavigation` to the chrome executable. Another alternative I haven't tried yet is using multi gesture libraries.

# Install native WeChat (Universal OS) on Ubuntu
- You need flatpak and flathub install on Debian: https://flathub.org/setup/Ubuntu:
```
sudo apt install flatpak
sudo apt install gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
- Then on Fedora/Ubuntu do the following:
```
flatpak install flathub com.tencent.WeChat
```
- To run wechat
```
flatpak run com.tencent.WeChat
```

TODO: some emoji fonts are missing


# Tune Gnome 3.x

To install extensions for Gnome 3.x, just search the add-ons in ```Software``` application,  then tune it on through ```Extension Settings```.

- [NoAnnoyance](https://github.com/sindex/no-annoyance) removes the “Windows is ready” notification and puts the window into focus.
- [Suspend Button](https://extensions.gnome.org/extension/826/suspend-button/) adds back the sleep/suspend button

# Resolve ```RAR``` Parsing filters unsupported error

You can use

```
sudo apt-get install unrar # support RAR 3
```

I recommend to install only one of these (unrar in my case). Then use archive manager:

```
sudo apt-get install file-roller
```

# Blur app on factional scaling
One may found chromium based or electron app blur when Gnome Wayland fractional scaling is enabled. To address it, you need to put `--ozone-platform=wayland` for app.

## Address VSCode blur
1. Append `--ozone-platform=wayland` option to `Exec` in `/usr/share/applications/code.desktop` (you can test run the option in terminal `code --ozone-platform=wayland`)
2. Change the title bar to custom (otherwise there's glitch between title bar and window decorator): `Window: Title Bar Style` > `Custom`.

## Address Chromium blur
> Warning: change `Preferred Ozone platform` in `chrome:flags` may cause browser flicking and broken. So use command line or change option on `/usr/share/applications/google-chrome.desktop`
will be much safer (since you can revert back without losing app data). Append the `--ozone-platform=wayland` to `Exec` or command line.
Without setting the ozone platform, Chrome's hangs a lot for me, making is basically unusable. (Constantly freezes for half a second while scrolling.)

Using the command line parameter worked nicely.

If anyone is reluctant to delete their ~/.config/google-chrome folder, you can simply edit your config manually when Chrome is not running. The config is in a JSON file called "Local State". Search for "ozone" and remove the corresponding key under "browser". (I think it was something like "lab_experiments" that I zapped.)



# Add 7z support
```sh
sudo apt-get install p7zip-full
```

# vscode [idea key binding](https://marketplace.visualstudio.com/items?itemName=k--kato.intellij-idea-keybindings)
One may find `ctrl+w` not work on Linux the shortcut has been defined to other feature. To restore it, just go to the `idea keybindings`' setting > `Extension Keyboard Shortcuts` > search for `ctrl+w` > `Remove Keybinding`.

# Install Pinta

- Open terminal with CTRL+ALT+T Add Pinta stable PPA repository:
```sh
sudo add-apt-repository ppa:pinta-maintainers/pinta-stable
```

- Update system package lists:
```sh
sudo apt update
```

- Install pinta
```sh
sudo apt install pinta
```

# Alternative screen capture using default shortcut
- ```Shift``` + ```prt sc sysrq``` to capture select area


# Get rid of resources greedy ```evolution-calendar*``` services on ```x205ta```
```shell
mv /usr/lib/evolution /usr/lib/evolution_DISABLE
for procname in $(ps aux | grep evolution | awk -F'/' '{print $NF}' | grep evolution | grep -v grep); do killall $procname; done
```

# Remove ```Parallel printer driver modules``` to improve performance and mute ```Failed to load kernel modules```

```Failed to load kernel modules``` is actually not a kernel issue, but a bug in the default configuration of CUPS (the printing system), which tries to load the drivers for the ancient parallel port (which this computer obviously doesn't have). You can easily solve it by commenting out ```/etc/modules-load.d/cups-filters.conf```, like so:

```sh
# Parallel printer driver modules loading for cups
# LOAD_LP_MODULE was 'yes' in /etc/default/cups
#lp
#ppdev
#parport_pc
```


# Visual Studio Code Settings

 ```
{
    "workbench.colorTheme": "Xcode_default"
     "window.zoomLevel": 1,
    "editor.fontFamily": "'Menlo', 'Consolas', 'DejaVu Sans Mono', 'monospace'",
}
 ```
To have a vertical line (vertical rulers) to control line length, set a ruler in
```settings.json``` as (in this case length is 80)
```
{
  "editor.rulers": [80]
}
```
For remote developing, install [Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) and copy public key to dev server by
```
ssh-copy-id [username]@[ip]
```

Markdown preview extension: ```Markdown all in one```



# Mac-like command: ```open``` for Ubuntu

```open``` command in mac is really convenient and its alias is xdg-open. However the xdg-open is not as smart as open in mac. Due to the fact of this, I wrote a handy script(in bin/open) for you to deal with it. You can place it under ```/usr/local/bin``` manually or install it by executing deploy as well.

# Apache

- Install ```Apache```
```sh
sudo apt install apache2
```

- Touch an website directory by
```sh
mkdir ~/apache_service_root
```

- Change ```/etc/apache2/sites-available/000-default.conf``` and ```/etc/apache2/apache2.conf``` from ```DocumentRoot /var/www/index``` to ```DocumentRoot /home/syscl/apache_server_root``` and from ```<Directory /var/www/>``` to ```<Directory /home/syscl/apache_server_root/>```

# Update for website
```sh
/etc/init.d/apache2 restart
```

# Update softwares through terminal

```sh
sudo apt upgrade
```

# CentOS/Ubuntu install ```netdata```
```Netdata``` is a powerful monitor tool set for developer to keep tracking of its servers, to install it on Ubuntu ```18.04+``` simply type in
```sh
apt install netdata
```
- On CentOS, please refer [here](https://github.com/firehol/netdata/wiki/Installation)

- To allow ANYONE to access netdata, change the ```bind socket to IP = 127.0.0.1``` to ```bind socket to IP = 0.0.0.0``` in ```/etc/netdata/netdata.conf```
- Start all the services by the following:
```sh
systemctl start netdata
ufw enable
ufw allow 19999/tcp
ufw reload
```
- Now access the netdata through ```http://your-server-ip:19999```

# Enable temperature for netdata
- Install ```lm_sensors``` through ```apt install lm_sensors```
- Uncomment ```# sensors=force``` in ```/etc/netdata/charts.d.conf```
- ```cp /etc/netdata/conf.d/python.d/sensors /etc/netdata/conf.d```
- Restart netdata by the following:
```sh
killall netdata
systemctl daemon-reload
systemctl enable netdata
systemctl restart netdata
```
- as a side note, we can actually execute ```sensors``` after install ```lm_sensors``` to check CPU temperature

# Check operating system archieture (32-bit vs 64-bit)
```sh
getconf LONG_BIT
```
# CentOS/RHEL install ```deltarpm``` for allowing the delat rpm function.

# CentOS/Ubuntu install ```nextcloud```

Please refer [here](https://www.howtoforge.com/tutorial/how-to-install-nextcloud-with-nginx-and-php-fpm-on-centos-7/). And don't forget to change ```php70w-*``` to ```php-*``` for the installation commands.
- Enable pretty urls (get rid of index.php*) append the following two lines in your ```[nextcloud root]/config/config.php```:
```
'overwrite.cli.url' => 'https://example.com/nextcloud',
'htaccess.RewriteBase' => '/nextcloud',
```
then execute ```sudo -u www-data php [nextcloud root]/occ maintenance:update:htaccess```

# CentOS 7/Ubuntu install ```phpVirtualBox```
- Add VirtualBox source by creating a file ```virtualbox.repo``` under ```/etc/yum.repos.d```:
```
[virtualbox]
name=Oracle Linux / RHEL / CentOS-$releasever / $basearch - VirtualBox
baseurl=http://download.virtualbox.org/virtualbox/rpm/el/$releasever/$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://www.virtualbox.org/download/oracle_vbox.asc
```
- Install VirtualBox by ```yum install virtualbox```
- Install [VirtualBox extension pack](https://www.virtualbox.org/wiki/Downloads) by ```VBoxManage extpack install [extension-pack-path]```
- Install [phpVirtualBox](https://github.com/phpvirtualbox/phpvirtualbox)
- Install subscript-manager
- Create a new file in ```/etc/default/virtualbox``` so that we can ```systemctl start vboxweb-service```, the line we have to add is: ```VBOXWEB_USER=root``` notice here the user is "the user as which vboxwebsrv will run.", in this case  ```root```, more information can be referred to [here](https://github.com/phpvirtualbox/phpvirtualbox/wiki/vboxweb-service-Configuration-in-Linux)
- Copy ```phpvirtualbox/config.php-example``` to ```phpvirtualbox/config.php``` and change the ```var $password = '*';``` as the password you want.
- Add a new user ```vbox``` by ```useradd vbox``` and its password is the same as in ```phpvirtualbox/config.php```'s ```var $password = '*';```
- Install epel repos
- Install php-soap, note if you have php 7.0 use ```yum install php70w-soap```
- Disable ```selinux```
- Find the path of soap through ```find -name soap.so```, usually it will be located at  ```/usr/lib64/php/modules/soap.so```
- Insert in in ```/etc/php.ini``` by a new line: ```extension='/usr/lib64/php/modules/soap.so'```
- Restart your ```httpd``` service by ```systemctl restart httpd```

# Install ```emby``` media server
Unlike ```$lex``` require money everywhere,  ```emby``` is an open source media server, like universal media server (ums on Sony PS4), the way to install is straightforward, but notice change the ```user``` and ```group``` as ```emby:emby``` for the folders you want to attach as libraries otherwise permission errors will occurs.

# Chrome extensions / Firefox add-ons
- [I still don't care about cookies](https://chrome.google.com/webstore/detail/i-still-dont-care-about-c/edibdbjcniadpccecjdfdjjppcpchdlm) to remove annoying cookie pops up

# CentOS/RHEL turn off beep/bell terminal sound
- Remove ```pcspkr``` kernel module
```sh
rmmod -v pcspkr
```
- Blacklist ```pcspkr``` in ```/etc/modprobe.d/blacklist``` by adding the following line:
```sh
blacklist pcspkr
```

# CentOS creates Wireless Hotspot by one line command

```sh
nmcli dev wifi hotspot ifname wlan0 ssid test password "test1234"
```

More details please refer [here](https://unix.stackexchange.com/questions/234552/create-wireless-access-point-and-share-internet-connection-with-nmcli)



# Ubuntu recovery mode mount root partition as read/write (rw)

mount -o remount,rw /


# How to use?

- Download this project by
```sh
git clone https://github.com/syscl/LinuxLand
```
- This will download the whole directory, the next step is to change the deploy permission so that it can be executed:
```sh
cd LinuxLand
chmod +x deploy
```
- Execute deploy by typing:
```sh
./deploy
```

## zsh and configuration

- Switch default shell `chsh -s $(which zsh)`
- Install [oh-my-zsh](https://ohmyz.sh/)
- Enable autosuggestion in `~/.zshrc` > `plugins` > `zsh-autosuggestions`:
```
plugins=(
        ...
        zsh-autosuggestions
)
```
- Install [powerlevel10k](https://github.com/romkatv/powerlevel10k), with patched `Meslo Nerd Font`.

# Enable ZRAM for ubuntu
On low memory machine, it will be benefit to enable memory compression (ZRAM is enabled by default on Fedora):
- Install zram: `sudo apt install zram-config`
- Enable zram:
```
systemctl enable zram-config
systemctl start zram-config
```
- Check the zram status by: `zramctl`. Also read some document about zswap.

# Install GraalVM on Fedora/Ubuntu
Please refer to this [link](https://gist.github.com/ricardozanini/fa65e485251913e1467837b1c5a8ed28).


[antiX Linux]
For pretty old hardware, antiX doing a great job, especially on iMac8,1(2008). I want to like puppy Linux, however it has screen flickering on iMac8,1.

See changelogs [here](https://github.com/syscl/LinuxLand/blob/master/Changelog.md)
