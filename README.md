# Plasma Systemd Control

This is a simple plasma applet for KDE Plasma 5 to control systemd services. It is not designed to be a complete user interface for systemd, but it provides an convenient way to start and stop selected services. 

### Supported Features
* start service (`sudo systemctl start SERVICE`)
* stop service (`sudo systemctl stop SERVICE`)
* updates automatically if status changed externally
* system units and user units (--user)

### Prerequisite
To work properly, you must be able to run `sudo systemctl` without password. Usually you can achieve this be editing `/etc/sudoers` with visudo.

### Installation
```
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kf5-config --prefix` -DCMAKE_BUILD_TYPE=Release -DLIB_INSTALL_DIR=lib -DKDE_INSTALL_USE_QT_SYS_PATHS=ON ../
make
make install
```
For Arch Linux there is a package available via AUR: https://aur.archlinux.org/packages/plasma5-applets-systemd/

### Dependencies (Debian)

* cmake
* linux-libc-dev
* build-essential
* extra-cmake-modules
* libkf5config-dev
* libkf5plasma-dev
* qt5-default
* qtdeclarative5-dev

### Dependencies (openSUSE)

* cmake
* extra-cmake-modules
* linux-glibc-devel
* libqt5-qtbase-devel

### Install and test
kpackagetool5 -t Plasma/Applet --install plasma-systemd-1.2.1/plasmoid
kpackagetool5 -t Plasma/Applet --upgrade plasma-systemd-1.2.1/plasmoid 
plasmoidviewer --applet org.kde.systemd-control
