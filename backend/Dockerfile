# Use the latest Rust image from Docker Hub as the base image
FROM rust:latest

# Set the working directory inside the container to /app
WORKDIR /app/

# Copy the contents of the current directory (host) to the working directory (container)
COPY . .

# Set the default Rust toolchain to the one specified in the rust-toolchain file
RUN rustup default

# Install the diesel_cli crate with the "postgres" feature, excluding default features
RUN cargo install diesel_cli --no-default-features --features postgres

# Install the cargo-watch crate to enable auto-reloading of the application on changes
RUN cargo install cargo-watch

# Expose port 8000 for the application to listen on
EXPOSE 8000

# Set the default command to run cargo-watch and display why the app is rebuilding on each change
CMD ["cargo", "watch", "--why", "--", "echo"]
