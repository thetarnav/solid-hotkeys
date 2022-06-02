# Solid Hotkeys - Cmd+S+H

[![Solid Hotkeys Banner](https://raw.githubusercontent.com/alekangelov/solid-hotkeys/main/hotkeys-banner.png)](https://alekangelov.github.io/solid-hotkeys)

<span class="badge-nodeico"><a href="https://www.npmjs.com/package/solid-hotkeys" title="Nodei.co badge"><img src="https://nodei.co/npm/solid-hotkeys.png?downloads=true&compact=true&height=2" alt="Nodei.co badge" /></a></span>
<br class="badge-separator" />
<br class="badge-separator" />
<span class="badge-shields"><img src="https://img.shields.io/badge/bundle-~2kb-teal.svg" /></span>
<span class="badge-npmversion"><a href="https://npmjs.org/package/solid-hotkeys" title="View this project on NPM"><img src="https://img.shields.io/npm/v/solid-hotkeys.svg" alt="NPM version" /></a></span>
<span class="badge-npmdownloads"><a href="https://npmjs.org/package/solid-hotkeys" title="View this project on NPM"><img src="https://img.shields.io/npm/dm/solid-hotkeys.svg" alt="NPM downloads" /></a></span>

Solid Hotkeys is the easiest way to add hotkeys to your application.
Built for and with [Solid](https://github.com/solidjs/solid).

## Motivation

You gotta have hotkeys in your app. It doesn't use timeouts and other stuff like that, but rather checks if the keys currently are pressed and in the right order.

## Installation

There are a couple of things you need to do to install Hotkeys.

```bash
# yarn
yarn add solid-hotkeys

# npm
npm i solid-hotkeys
```

and presto you can get to hotkeying.

## Usage

The API is pretty simple and extensively types, so it's going to be really hard to mess it up, but here are a couple of examples:

## Basic

```tsx
const opposite = (prev: boolean) => !prev;

const Basic = () => {
  const [show, setShow] = createSignal(false);

  useHotkeys(['Meta', 'P'], () => {
    setShow(opposite);
  });

  return (
    <Show when={show()} fallback={"I'm not shown"}>
      I'm shown now
    </Show>
  );
};
```

## Wildcard usage

Wildcard usage is really if you need to do some super insane stuff with the presses. Maybe someone's going to need it, so I added it in v1. If you pass in "\*" as the key array, it's going to fire on every key

```tsx
const Wildcard = () => {
  const [keys, setKeys] = createSignal([]);
  useHotkeys(['*'], currentlyPressed => setKeys(currentlyPressed));

  return (
    <div>
      <For each={keys()}>{item => <kbd>{item()}</kbd>}</For>
    </div>
  );
};
```

### NOTE: THE CURRENTLY PRESSED KEYS ARE ALL UPPERCASE BECAUSE OF NORMALIZATION

## Types

You can also import the types so you can have stricter typing in your app!

```ts
import type {
  HotkeyArray,
  NormalizedKeys,
  HotkeyEvent,
  HotkeyCallback,
} from 'solid-hotkeys';
```

- HotkeyArray -> what useHotkeys expects -> an array of all the normalized keys
- Normalized Keys -> All of the keys that are maybe on a keyboard, uppercased
- HotkeyEvent -> a stricter event where keys are strictly typed.
- HotkeyCallback -> what the callback for the createHotkey function is

## Closing notes

Report bugs, features and such and let's get this party started.

Cheers,
-Alek
