# GEMINI.md

## Project Overview

This directory contains a Nix configuration for managing a user's home environment using [Home Manager](https://github.com/nix-community/home-manager) and [Nix Flakes](https://nixos.wiki/wiki/Flakes).

*   `flake.nix`: Defines the flake's inputs (dependencies) like `nixpkgs` and `home-manager`, and specifies the output structure, pointing to `home.nix` for the main configuration.
*   `home.nix`: Contains the core Home Manager configuration for the user `deck`. This is where packages, dotfiles, services, and environment variables are defined.
*   `flake.lock`: A generated file that pins the exact versions of the flake's inputs, ensuring reproducible builds.

The primary purpose of this setup is to provide a declarative, reproducible, and version-controlled home environment.

## Building and Running

The configuration is managed using standard Nix and Home Manager commands.

*   **Apply the configuration:** To activate the configuration defined in `home.nix`, run the following command from this directory:
    ```bash
    home-manager switch
    ```

*   **Update Dependencies:** To update the flake's inputs (like `nixpkgs` and `home-manager`) to their latest versions, run:
    ```bash
    nix flake update
    ```
    After updating, you must run the `switch` command again to apply the changes.

*   **Inspect the Flake:** To see the outputs and structure defined by the flake, use:
    ```bash
    nix flake show
    ```

## Development Conventions

*   **Configuration:** All user-specific configuration (packages, files, etc.) should be added to `home.nix`.
*   **Dependencies:** Flake inputs and the overall structure are managed in `flake.nix`.
*   **Packages:** Packages are installed by adding them to the `home.packages` list within `home.nix`.
*   **Secrets:** This configuration does not appear to have a dedicated secrets management solution. Avoid storing sensitive information directly in these files.
