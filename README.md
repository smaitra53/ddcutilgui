# ddcutilgui

A simple GTK frontend for controlling monitor brightness with [`ddcutil`](https://www.ddcutil.com/).

## Features

- Adjust monitor brightness from a graphical interface

- Displays the current brightness level

- Applies brightness changes using `ddcutil`

## Motivation

I was tired of using the awful OSD controls on my Samsung S27D850T monitor to adjust the monitor brightness.

## Requirements

- GTK 4
- Python 3.10+
- PyGObject
- [`ddcutil`](https://www.ddcutil.com/)

**Note:** 
Your monitor must support DDC/CI for `ddcutil` to communicate with it.
The application uses VCP code `0x10` (Brightness) to control the monitor.
You can also verify that `ddcutil` can communicate with your monitor directly:

```bash
ddcutil getvcp 10
```

## Installation

Clone the repository:

```bash
git clone https://github.com/smaitra53/ddcutilgui.git
cd ddcutilgui
```

Install the required dependencies using your distribution's package manager.

For Debian/Ubuntu:

```bash
sudo apt install python3-gi python3-gi-cairo gir1.2-gtk-4.0
```

For Fedora:

```bash
sudo dnf install python3-gobject gtk4
```

For other distributions, consult [PyGObject documentation](https://pygobject.gnome.org/getting_started.html)

Then run:

```bash
chmod +x ddcutilgui
mkdir -p ~/.local/bin
cp ddcutilgui ~/.local/bin/
mkdir -p ~/.local/share/applications
cp monitor-brightness.desktop ~/.local/share/applications
```

**Note:** Make sure ~/.local/bin is in path.

## Usage

Launch the application and adjust the brightness slider to the desired level.

Click **Apply** to send the new brightness value to the monitor.

`ddcutilgui` is designed for mouse-based interaction and avoids combining mouse and keyboard controls, hence the lack of an input box.
